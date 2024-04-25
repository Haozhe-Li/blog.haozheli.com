# CS 340 Midterm 3

All from practice



## Multiple Choice

| Algorithm                                        | Input                               | Output                                                       | Keys                                                         |
| :----------------------------------------------- | ----------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Symmetric cipher                                 | An arbitrary-length string of bytes | A string of bytes whose length depends on the input length   | A shared private key, known to the communicating parties but no one else |
| Asymmetric cipher                                | A fixed-sized bitvector             | A fixed-sized bitvector                                      | A private key known only to one party and a public key available to anyone |
| Digital signature                                | An arbitrary-length string of bytes | A fixed-sized bitvector                                      | A private key known only to one party and a public key available to anyone |
| Cryptographically-secure hash                    | An arbitrary-length string of bytes | A fixed-sized bitvector                                      | None; this algorithm doesn't use keys                        |
| Cryptographically-secure random number generator | It has no input                     | A bitvector whose size can be selected as an independent free parameter, not fixed by either the algorithm nor the input | None; this algorithm doesn't use keys                        |
| Key exchange                                     | It has no input                     | A bitvector whose size can be selected as an independent free parameter, not fixed by either the algorithm nor the input | Several private keys, one for each of the communicating parties |



## Coding

````python
from flask import Flask, request, jsonify
import threading
app = Flask(__name__)

balance = 0
balance_lock = threading.Lock()
balance_condition = threading.Condition(balance_lock)

@app.get('/peek')
def peek():
  """GET /peek returns the current account balance as a string, like "340".
  The balance is initially 0, but can be changed by the other API
  endpoints."""
  with balance_lock:
    return str(balance)

@app.get('/deposit/<amount>')
def deposit(amount):
  """GET /deposit/340 adds 340 to the current account balance and returns the
  new balance as a string. This should work for any postiive integer, not just
  340. It should return status code 400 for a negative or non-integer
  argument."""
  global balance
  try:
    amount = int(amount)
  except:
    return "non-integer value", 400
  if isinstance(amount, int) == False:
    return "non-integer value", 400
  if amount < 0:
    return "negative value", 400

  with balance_lock:
    balance += amount
    balance_condition.notify_all()
  return str(balance)

@app.get('/withdraw/<amount>')
def withdraw(amount):
  """>GET /withdraw/340 removes 340 to the current account balance and returns
  the new balance as a string. If there are insufficient funds, it waits until
  the funds become available before returning (i.e., waits until a separate
  API callthread deposits funds), and does so efficiently (i.e., not a busy or
  time-based wait). This should work for any postiive integer, not just 340.
  It should return status code 400 for a negative or non-integer argument."""
  global balance
  try:
    amount = int(amount)
  except:
    return "non-integer value", 400
  if amount < 0:
    return "negative value", 400

  with balance_condition:
    while balance < amount:
      balance_condition.wait()
    balance -= amount
  return str(balance)


if __name__ == '__main__':
    app.run(debug=True)
````



