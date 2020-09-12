call plug#begin()  

Plug 'dart-lang/dart-vim-plugin'  
Plug 'rust-lang/rust.vim'  
Plug 'mhartington/oceanic-next'  
Plug 'Rigellute/rigel'  
Plug 'vim-airline/vim-airline'  

call plug#end()  
nmap <silent> <C-k> :wincmd k<CR>  
nmap <silent> <C-j> :wincmd j<CR>  
nmap <silent> <C-h> :wincmd h<CR>  
nmap <silent> <C-l> :wincmd l<CR>   
map <F6> :!cargo build<CR>  
map <F7> :!cargo run<CR>   
map <F8> :!rustup run nightly cargo bench<CR>  
map <F9> :!wasm-pack build --debug<CR>  

"Commenting blocks of code.  
augroup commenting_blocks_of_code  
  autocmd!  
  autocmd FileType c,cpp,java,scala,rust let b:comment_leader = '// '  
  autocmd FileType sh,ruby,python   let b:comment_leader = '# '  
  autocmd FileType conf,fstab       let b:comment_leader = '# '  
  autocmd FileType tex              let b:comment_leader = '% '  
  autocmd FileType mail             let b:comment_leader = '> '  
  autocmd FileType vim              let b:comment_leader = '" '  
augroup END  
noremap <silent> ,cc :<C-B>silent <C-E>s/^/<C-R>=escape(b:comment_leader,'\/')<CR>/<CR>:nohlsearch<CR>  
noremap <silent> ,cu :<C-B>silent <C-E>s/^\V<C-R>=escape(b:comment_leader,'\/')<CR>//e<CR>:nohlsearch<CR>  

set number  
set visualbell  
set noerrorbells  
set t_vb=  
set tabstop=4  
set shiftwidth=4  
set expandtab  
set backspace=2  
let g:rigel_airline = 1  
let g:airline_theme = 'rigel'  
set termguicolors  
syntax enable  
colorscheme rigel  
