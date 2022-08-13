# Theory of ConnTrack

With the 1.1 concepts in mind, let’s reasons about the underlying theory of connction tracking.

To track the states of all connections on a node, we need to,

1. **Hook (or filter) every packet** that passes through this node, and analyze the packet.
2. **Setup a “database”** for recoding the status of those connections (conntrack table).
3. **Update connection status timely** to database based on the extracted information from hooked packets.

For example,

1. When hooked a TCP SYNC packet, we could confirm that a new connection attempt is under the way, so we need to create a new conntrack entry to record this connection.
   When got a packet that belongs to an existing connection, we need to update the conntrack entry statistics, e.g. bytes sent, packets sent, timeout value, e.g.
2. When no packets match a conntrack entry for more than 30 minutes, we consider to delete this entry from the database.
   Except the above functional requirements, performance requirements also also deserve our concern, as conntrack module filters and analyzes every single packet.
3. Performance considerations are fairly important, but they are beyond the scope of this post. We will come back to performance issues again when walking through the kernel conntrack implementation later.

Besides, it’s better to have some management tools to faciliate the using of conntrack.
