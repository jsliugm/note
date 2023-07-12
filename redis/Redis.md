# Redis

## Eval

### 统计key占用空间

lua脚本

```lua
local sum = 0
local keys = redis.call("SCAN", ARGV[1],ARGV[2],ARGV[3])
for _, key in ipairs(keys[2]) do
  if string.match(key, ARGV[4]) then
    sum = sum + redis.call("MEMORY", "USAGE", key)
  end
end
return sum
```

命令执行lua

```shell
#统计key中包含Ex占用空间
EVAL "local sum = 0 local keys = redis.call(\"SCAN\", ARGV[1], ARGV[2], ARGV[3]) for _, key in ipairs(keys[2]) do if string.match(key, ARGV[4]) then sum = sum + redis.call(\"MEMORY\", \"USAGE\", key) end end return sum" 0 0 MATCH *Ex* Ex
```

