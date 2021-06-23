# jq

- JQ is a commandline JSON processor

```shell
# Format the JSON pretty
echo '{"foo": 0}' | jq .

# Save JSON into environment variable
var=$(jq -n --arg b "$bar" '{
  Comment: "Update DNSName.",
  Changes: [
    {
      Action: "UPSERT",
      ResourceRecordSet: {
        Name: "alex.",
        Type: "A",
        AliasTarget: {
          HostedZoneId: "######",
          DNSName: $b,
          EvaluateTargetHealth: false
        }
      }
    }
  ]
}')

# Thousand fields JSON
thousandone_fields_json=$(echo {1..1001..1} | jq -Rn '( input | split(" ") ) as $nums | $nums[] | . as $key | [{key:($key|tostring),value:($key|tonumber)}] | from_entries' | jq -cs 'add')

echo "$thousandone_fields_json"
```
