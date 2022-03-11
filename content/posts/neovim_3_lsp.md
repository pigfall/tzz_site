---
title: "🌸 Neovim: LSP"
date: 2022-03-10T16:38:54+08:00
draft: false
thumbnail: "images/nvim_lsp_ss.png"
series: 
  - nvim
---
  LSP will give your neovim the abilities like auto completion, jump to definition etc...
  
  ### Screenshot for auto completion and jumping to definition
  ![Screenshot](/images/nvim_lsp_screenshot_comp_jump_def.gif)
  
  
  ### Modify your vim-plug in init.vim
  ```vim
  " in init.vim, NOTE: this plugin requires nodejs
  Plug 'neoclide/coc.nvim', {'branch': 'release'}
  ```
  
  ### Config with some helper functions 
  ```vim
  " in init.vim
lua << EOF
  
  -- check buffer if modified
  function buffer_modified()
      return vim.bo.modified
  end
  
  local vimfn = vim.fn
  -- split the window if buffer modified before jump to definition
  function tzzJumpToDef(doJump,doBeforeJump)
      print("tzzJumpToDef")
      if buffer_modified() and (vimfn.len(vimfn.win_findbuf(vimfn.bufnr('%'))) < 2 ) then
    vim.cmd("normal -vs<CR>")
      end
      -- vim.lsp.buf.definition()
      if doBeforeJump then
        doBeforeJump()
      end
      doJump()
  end
  
  
  -- wrap coc jump definition
	function tzz_coc_jump_def_wrapper()
		vim.cmd("call CocActionAsync('jumpDefinition')")
	end
  
  -- our entry point of jumping definition
	function tzz_coc_jump_def()
		tzzJumpToDef(tzz_coc_jump_def_wrapper)
	end
EOF

  "  languages we expected to enable our hotkey
  let lang_list = ["go,dart,rust"]
  " our coc autogroup
  augroup tzz-coc
    au! 
    exec "autocmd FileType " . join(lang_list,",") . " inoremap <silent><expr> <c-o> coc#refresh()"
    exec "autocmd FileType " . join(lang_list,",") . " nmap <buffer> <c-]> :lua tzz_coc_jump_def()<CR>"
    exec "autocmd FileType " . join(lang_list,",") . " nmap <buffer> <c-n> <Plug>(coc-diagnostic-next)" 
  augroup end
  ```
  
  
