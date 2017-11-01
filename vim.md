Vim-Go
======
vif ==> indent funtion combine with d, y etc....
vaf ==> the all funtion including the comments.
gs ===> convert single line to multi line, but the cursor on the parragh 
Estos no me estan funcionando me parece que se necesita snippet.
errp ==> snippet && TAB with panic.
errn ===> return error.
errn, ===> pick the return you want.
func ===> create a funtion
fn ===> fmt.Println("")
ff ====> better.
json ====> `"json:"ports"`
GoAddTags hace lo mismo para muchos mas.
GoVet More precision about errors.
Existe un stack de LINTS llamado GoMetaLinter
GoAlternate ===> Llama al Test file del archivo que tenemos, si lo lanzamos
otra vez volvemos al file anterior.
        Unos shotcuts serian AS: normal
                             AV: Open Vertical
GoDef  or gd===> Va a la def de la funcion
GoDefPop C t ==> GO back
PARA ESTO SE NECESITA ctrp.vim
GoDcls ===> Hace un sumario y muestra todas las funciones y sus type
declaration, tambien tiene fuzzy word search.
GoDeclsDir ==> Es similar pero busca en diff files.
]] ===> Change to the next funtion
[[ ===> Reverse
Tambien funciona con los operators, c, y, p, d
GoDoc "K" ===> Split Vertical info about a funtion.
GoInfo ===> Show the args and the types for the funtion.
GoRename ===> Could change the var name and everytime she get call, even
exported files.
Existe una herramienta llamada Go Guru que al parecer es bastante buena
GoReference ==> Nos muestra por ejemplo donde se uso los handlers, HttpRequest
en muchos archivos.
GoDescribe ===> Es bastante util tambien.
GoSameIds ===> muestra los ids utilizados.
GoSameIdsClear 
GoSameIdsAutoToggle
GoInplement ===> puedes usarlo en un interface para ver quien lo usa.
GoCallers ===> Te dice quien esta llamando a la funcion.
GoPlay ===> Send the selected code to go playground ALSO copy the url from
playground XD.


Mastering VIM
==============
* helpgrep util cuando no sabemos que estamos buscando.
* Cnext Shortcuts ?
      nnoremap ]q :cnext<cr>zz
      nnoremap [q :cprev<cr>zz
      nnoremap ]l :lnext<cr>zz
      nnoremap [l :lprev<cr>zz
* cnfile cpfile jump to another page ex: ManPage.
* Damian option
      nmap <silent> <RIGHT>         :cnext<CR>
      nmap <silent> <RIGHT><RIGHT>  :cnf<CR><C-G>
      nmap <silent> <LEFT>          :cprev<CR>
      nmap <silent> <LEFT><LEFT>    :cpf<CR><C-G>
* vimgrep me permite usar grep en vim, el primer match carga como buffer en vim
y podemos ir saltando con cnext.
* Para usar un atajo usamos CTRL-] y nos devolvemos con CTRL-T
* anything in vertical bars is a hyperlink (CTRL-])
* tiene un code que abre todos los help page en un tag.
* EXERCISE, MIRA TODAS LAS KEY DE TU TECLADO A VER CUAL ES UTIL, Y UTILIZALAS
  POR UN TIEMPO, aprender vim lleva TIEMPO.
    - help normal-index
    - help insert-index
