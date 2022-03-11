---
title: "🌸 Neovim: Directory tree"
date: 2022-03-10T16:31:24+08:00
draft: false
thumbnail: "images/nvim_ss_nerdtree.png"
series: 
  - nvim
---
  Sometimes we need exploring files in directory tree which is more clearly to let us know the project  struct
  
  ![Like this](/images/tenor_1.gif)
  
  ### Modify your vim-plug in init.vim
  ```vim
  " in init.vim
  Plug 'scrooloose/nerdtree'
  ```
  
  ### Config hotkey
  ```vim
  "in init.vim
  
  " open directory tree
  nnoremap <Leader>nn :NERDTree<CR>
  
  " close directory tree
  nnoremap <Leader>nc :NERDTreeClose<CR>
  
  " toggle directory tree
  nnoremap <s-e> :NERDTreeToggle<CR>
  
  
  " Focus the current buffer in the directory tree
  nnoremap <Leader>nf :NERDTreeFind<CR>
  ```
  
  
  

