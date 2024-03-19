### 1. Things to Avoid

#### 1.1 Implicit State
- Implicit state in functions or data structures can lead to unexpected behavior when accessed concurrently by multiple threads.
- Using functions like `strtok` with hidden internal state can result in data being shared between threads, causing incorrect behavior.
- Reentrant functions, like `strtok_r`, are preferred as they do not use hidden state, requiring users to pass in state variables explicitly.

#### 1.2 Data Race
- Data races occur when one thread updates a variable while another thread is using it, leading to inconsistent or incorrect results.
- Synchronizing access to shared data is necessary to avoid data races.

#### 1.3 Deadlock
- Deadlock occurs when each thread is waiting for something that can't happen until another thread stops waiting, forming a cycle in the waiting-for relation.
- Deadlock conditions include mutual exclusion, hold and wait, no preemption, and circular wait.
- Examples include the "High-value exchange" scenario and the "Dining Philosophers" problem.

#### 1.4 Livelock
- Livelock occurs when threads do not make progress because their actions are not aligned with each other.
- It can occur when trying to remove deadlock by having threads try alternative actions.
- Example scenarios include situations where individuals repeatedly try to pass each other without success.

#### 1.5 Starvation
- Starvation occurs when one or more threads never make progress despite others doing so.
- It can result from synchronization designs that prioritize certain threads over others.
- Example scenarios include asymmetric workloads where threads requesting fewer resources consistently gain access over those requesting more.

### 2. Examples

#### 2.1 Lock ordering
- Deadlock prevention strategy involving imposing a total order on locks and acquiring them in that order.
- Ensures that cycles in the waiting-for relation cannot occur.

#### 2.2 Lock the locks
- Deadlock prevention strategy involving the use of additional locks to prevent cycles.
- Requires threads to acquire a "lock-acquiring lock" before obtaining other locks.

#### 2.3 Message queues
- Strategy to avoid data races by not allowing threads to access shared data directly.
- Threads communicate by passing messages through thread-safe queues, avoiding the need for locks.

#### 2.4 Optimistic transactions
- Approach to ensure atomicity of operations without using locks.
- Transactions check and finalize their changes after performing operations, rolling back if conflicts are detected.
- Provides a faster alternative to lock-based thread safety when conflicting updates are rare.

This summary captures the essence of the text, highlighting the key concepts and strategies discussed in each section.