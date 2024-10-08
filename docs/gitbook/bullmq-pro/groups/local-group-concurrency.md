# Local group concurrency

It is also possible to set a specific concurrency value to a given group. This is useful if you require that different groups should run with different concurrency factors.

Please keep in mind that when specifying a group's concurrency factor, you are storing this value in Redis, so it is your responsibility to remove it if you are not using it anymore.

You can use the `setGroupConcurrency` method like this:

```typescript
import { QueuePro } from '@taskforcesh/bullmq-pro';

const queue = new QueuePro('myQueue', { connection });
const groupId = 'my group';
await queue.setGroupConcurrency(groupId, 4);
```

{% hint style="warning" %}
Make sure to also set the [Group Concurrency](concurrency.md) at the worker instance level along side with the desired local concurrency, as it is required for this feature to function properly and also will act as a default concurrency value for the groups that have no local concurrency defined.
{% endhint %}

And you can use the `getGroupConcurrency` method like this:

```typescript
const concurrency = await queue.getGroupConcurrency(groupId);
```

## Read more:

- 💡 [Set Group Concurrency API Reference](https://api.bullmq.pro/classes/v7.Queue.html#setGroupConcurrency)
- 💡 [Get Group Concurrency API Reference](https://api.bullmq.pro/classes/v7.Queue.html#getGroupConcurrency)
