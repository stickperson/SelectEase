## SelectEase.nvim

Select text using Treesitter Queries and start typing right away.

https://user-images.githubusercontent.com/102876811/219462863-d004636c-f7b6-4556-8cc6-45845b3aa668.mp4

## Word of Caution:

Please be aware that this plugin is still in an experimental stage and may exhibit unexpected behavior.
Your feedback and suggestions are welcome and please feel free to create issues or pull requests on the project's GitHub repository.
I appreciate your willingness to try it out the plugin and share your thoughts.

## Installation:

Example `lazy.nvim` config:

```lua
return {
    "ziontee113/SelectEase",
    config = function()
        local select_ease = require("SelectEase")

        -- example query
        local query = [[
            ;; query
            ((identifier) @cap)
            ("string_content" @cap)
            ((true) @cap)
            ((false) @cap)
        ]]

        -- next / previous node that matches the query
        vim.keymap.set({ "n", "s", "i" }, "<C-A-p>", function()
            select_ease.select_node({ query = query, direction = "previous" })
        end, {})
        vim.keymap.set({ "n", "s", "i" }, "<C-A-n>", function()
            select_ease.select_node({ query = query, direction = "next" })
        end, {})

        -- "vertical drill jump"
        vim.keymap.set({ "n", "s", "i" }, "<C-A-k>", function()
            select_ease.select_node({
                query = query,
                direction = "previous",
                vertical_drill_jump = true,
            })
        end, {})
        vim.keymap.set({ "n", "s", "i" }, "<C-A-j>", function()
            select_ease.select_node({
                query = query,
                direction = "next",
                vertical_drill_jump = true,
            })
        end, {})

        -- jump to targets only on current line
        vim.keymap.set({ "n", "s", "i" }, "<C-A-h>", function()
            select_ease.select_node({
                query = query,
                direction = "previous",
                current_line_only = true,
            })
        end, {})
        vim.keymap.set({ "n", "s", "i" }, "<C-A-l>", function()
            select_ease.select_node({
                query = query,
                direction = "next",
                current_line_only = true,
            })
        end, {})
    end,
}
```

## Feedback is always appreciated 

If you encounter any issues or have suggestions for improving the plugin, please feel free to open an issue or pull request.
