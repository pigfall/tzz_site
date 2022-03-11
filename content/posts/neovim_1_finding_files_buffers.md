---
title: "🌸 Neovim: Fuzzly finding files and buffers"
date: 2022-03-09T23:03:36+08:00
draft: false
thumbnail: "images/neovim_amway_thumbnail.png"
tags : [
"nvim",
]
series: 
  - nvim
---
  ## Fuzzly finding files by name 🎉  .
  
  It is too slow to find file in the direcotry tree.
  
  Fuzzly finding file by name makes you more sufficient
  
  ![Like this](/images/tenor_1.gif)
  

  We will use the telescope to impl the feature of fuzzly finding files
  
  ### Modify your vim-plug in init.vim
  ```vim
  " in init.vim
  Plug 'nvim-telescope/telescope.nvim'
  ```
  
  ### Config shortkey
  ```vim
  let mapleader="-"
  " fuzzly finding files
  nnoremap <Leader>f <cmd>Telescope find_files<cr>
  " fuzzly finding buffers
  nnoremap <Leader>b <cmd>Telescope buffers<cr>
  ```
