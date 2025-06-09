#	--de2e_subscribers_dump

##	Description
This command dumps the list of subscribers for Dynamic Edge-to-Edge (DE2E) tunnels. DE2E allows VeloCloud Edges to dynamically establish direct tunnels with other peer Edges when user traffic destined for those peers is detected, optimizing traffic flow and reducing latency. This command helps in troubleshooting and verifying DE2E tunnel establishment and subscriber information.

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --de2e_subscribers_dump
{
  "de2e_entries": []
}
```

##  Field descriptions
| Field          | Description                                                                 |
|----------------|-----------------------------------------------------------------------------|
| `de2e_entries` | An array containing the list of Dynamic Edge-to-Edge subscriber entries. Each entry would typically represent a peer Edge that has subscribed to or established a DE2E tunnel. If empty, as in the example, it indicates no active DE2E subscribers at the time of the command execution. |