Ответы по домашнему заданию "Инструменты Git".
```
1. Найдите полный хеш и комментарий коммита, хеш которого начинается на aefea.
Командой git show aefea находим нужный коммит.

2. Ответьте на вопросы.

  -Какому тегу соответствует коммит 85024d3?
  Командой git tag --points-at 85024d3 получил тег v0.12.23

  -Сколько родителей у коммита b8d720? Напишите их хеши.
  Командой git show b8d720 выяснил, что у него 2 родителя и их короткие хэши
  Командой git rev-parse 56cd7859e0 9ea88f22fc получил их полные хеши
  56cd7859e05c36c06b56d013b55a252d0bb7e158
  9ea88f22fc6269854151c571162c5bcf958bee2b

  -Перечислите хеши и комментарии всех коммитов, которые были сделаны между тегами v0.12.23 и v0.12.24.
  Командой git log v0.12.23..v0.12.24 получил все хеши и комментарии, но это неудобно, поэтому использовал git log --oneline v0.12.23..v0.12.24 и получил короткие хэши и комментарии:

33ff1c03bb (tag: v0.12.24) v0.12.24
b14b74c493 [Website] vmc provider links
3f235065b9 Update CHANGELOG.md
6ae64e247b registry: Fix panic when server is unreachable
5c619ca1ba website: Remove links to the getting started guide's old location
06275647e2 Update CHANGELOG.md
d5f9411f51 command: Fix bug when using terraform login on Windows
4b6d06cc5d Update CHANGELOG.md
dd01a35078 Update CHANGELOG.md
225466bc3e Cleanup after v0.12.23 release


  -Найдите коммит, в котором была создана функция func providerSource, её определение в коде выглядит так: func providerSource(...) (вместо троеточия перечислены аргументы).
  Командой git grep -n 'func providerSource' нашёл файл, в котором есть эта функция. Это provider_source.go
  Командой git log -L :providerSource:provider_source.go получил коммит в котором функция была создана. Он самый ранний по дате. (2 апреля 2020). 8c928e83589d90a031f811fae52a81be7153e82f 

  -Найдите все коммиты, в которых была изменена функция globalPluginDirs.
  Командой git log -L :globalPluginDirs:plugins.go получил все коммиты, в которых изменялась функция:

78b122055 Remove config.go and update things using its aliases
52dbf9483 keep .terraform.d/plugins for discovery
41ab0aef7 Add missing OS_ARCH dir to global plugin paths
66ebff90c move some more plugin search path logic to command
8364383c3 Push plugin discovery down into command package


  -Кто автор функции synchronizedWriters?
  Командой git log -S'func synchronizedWriters' --oneline нашёл коммиты, где появилась функция
  bdfea50cc8 remove unused
  5ac311e2a9 main: synchronize writes to VT100-faker on Windows
  Однако т.к. в 1м её удалили (судя по комментарию), остаётся 2й.
  Командой git show 5ac311e2a9 выясняем кто автор.
  Martin Atkins <mart@degeneration.co.uk>
  
```
