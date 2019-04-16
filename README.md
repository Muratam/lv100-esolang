# LV100POEM

lv100 poem language.

```
せかいがおわるさいごのひ
なんてことないにちようび
ぼくはこどもになっていて
ひとりでしずかにうたいだす
するとそらにはしろいくも
せかいをおおってあめがふる
ひとつぶあたるとくずれだし
ふたつぶあたるといろがぬけ
みつぶあたるといなくなる
はめつのうたがおわるとき
くるまもいえもにんげんも
みんなきえていなくなる
さいごにのこるぼくひとり
そらへととんでいなくなる

せかいのおわり、さようなら
```



## spec
memory size: 2019+

`ptr`: memory pointer. initial is 0. This should be between 0 and 2018.

## instructions
| opcode | function | behavior |
|--------|----------|----------|
|`%d`つぶあたるとくずれだし| FOCUS `N` | `ptr` := `N` |
|せかいがおわるさいごのひ| GETC | *ptr := getc() |
|なんてことないにちようび| PUTC | putc(*ptr) |
|ひとりでしずかに| GETN | scanf("%d", ptr) |
|するとそらには| PUTN | printf("%d", *ptr) |
|しろいくも| INC | *ptr++ |
|`%s`へととんでいなくなる| JGZ | jump to label:`%s` if *ptr > 0 |
|`%s`がおわるとき| LABEL | put label `%s` |
|くるまもいえもにんげんも| DEC | *ptr-- |
|みんなきえていなくなる| ZERO | *ptr := 0 |
|さいごにのこるぼくひとり| EXIT | exit() |
|`%s`はこどもになっていて| JZ | jump to label:`%s` if *ptr == 0|
|せかいのおわり| NEG | *ptr *= -1 |
|さようなら| ADD | *ptr = *(ptr+1) + *(ptr+2) |
|せかいをおおって| SUB | *ptr = *(ptr+1) - *(ptr+2) |
|あめがふる| MUL |*ptr = *(ptr+1) * *(ptr+2) |
|うたいだす| DIV |*ptr = *(ptr+1) / *(ptr+2); *(ptr+1) = *(ptr+1) % *(ptr+2) |

## notes
- GETC returns -1 when iwashi fails to read char. (eg. EOF)

## error code
- そんな時代は無い
    memory ptr should be between 0 - 2019

- そんな命令は無い
    invalid opecode
