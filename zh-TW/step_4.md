## 重力和跳躍

現在，你將讓角色的移動變得更逼真：你將為遊戲增加「重力」，還有給予角色「跳躍」的能力。

--- task ---

啟動遊戲，移動你的角色，試著讓它離開平台。 你看到了嗎？它竟然可以浮在半空中？！

![截圖](images/dodge-no-gravity.png)

--- /task ---

--- task ---

這一點也不科學，所以我們要為遊戲空間製造重力。 我們先創建一個名為 `重力`{:class="block3variables"}的變數。

[[[generic-scratch3-add-variable]]]

你可以視情況在舞台顯示或隱藏變數和它的值。

![截圖](images/dodge-gravity-annotated.png)

--- /task ---

--- task ---

添加這些程式積木來製造重力，先將`重力`設定為負數，並使用 `重力`的值重複改變角色的 y 座標：

![正在走路的 Pico](images/pico_walking_sprite.png)

```blocks3
    when flag clicked
	set [重力 v] to [-4]
	forever
		change y by (重力)
	end
```

--- /task ---

--- task ---

點擊綠旗，把你的角色拖曳到舞台的頂部，然後放開滑鼠按鍵。 看到了嗎？ 你為遊戲空間創造出地心引力了！

![截圖](images/dodge-gravity-drag.png)

--- /task ---

--- task ---

角色有重力了，但也不能直接穿過平台或梯子吧！ 加入一個新的`如果`{:class="block3control"}積木到程式裡，讓角色的重力只有浮在半空中時才生效。 這個重力的程式看起來會像這樣：

![正在走路的 Pico](images/pico_walking_sprite.png)

```blocks3
    when flag clicked
	set [重力 v] to [-4]
	forever
		if < not < <touching color [#0000FF]?> or <touching color [#FF69B4]?> > > then
			change y by (重力)
		end
	end
```

--- /task ---

--- task ---

再測試遊戲一下，看看現在重力是否如你預期那樣的運作。 當你的角色接觸平台或梯子時，它會不會停止往下墜？ 不過有時候它會卡在平台或梯子裡，你能想到要怎麼樣讓角色「剛好」落在平面的上方嗎？

![截圖](images/dodge-gravity-test.png)

--- /task ---

--- task ---

現在，我們來添加一些程式，讓玩家在按下<kbd>空白鍵</kbd>時，遊戲角色會跳起來。 有個非常簡單的寫法，就是讓角色重複向上移動多次：

![正在走路的 Pico](images/pico_walking_sprite.png)

```blocks3
    when [space v] key pressed
	repeat (10)
		change y by (4)
	end
```

由於重力導致角色不斷的被向下拉 `4` 個像素點，因此角色跳起來時，`y 改變`{:class="block3motion"} 的量必須要大於 4。 你可以試試不同的值，直到你對角色跳起來的高度滿意為止。

--- /task ---

--- task ---

測試你的程式。 你注意到了嗎，跳躍的動作看起來很不流暢。 為了讓跳的動作更像真的，你要把角色跳起來的距離愈縮愈短，直到跳到不能再高。

--- /task ---

--- task ---

要做到這個，你要先創建一個新變數，將它命名為`彈跳力`{:class="block3variables"}。 你一樣可以視情況決定是不是要隱藏這個變數。

--- /task ---

--- task ---

找到剛剛為角色寫的跳起來的程式，刪除它，改寫成這樣：

![正在走路的 Pico](images/pico_walking_sprite.png)

```blocks3
    when [space v] key pressed
	set [彈跳力 v] to [8]
	repeat until < (彈跳力) = [0] >
		change y by (彈跳力)
		change [彈跳力 v] by (-0.5)
	end
```

這個程式會讓你的角色往上方移動 8 像素，然後變成 7.5 像素，再變成 7 像素…慢慢的移動間隔愈來愈短，直到間隔變成 0，也就是不再跳高。 這樣子做是為了讓跳躍的動作看起來更加的平順，更符合真實的情況。

--- /task ---

--- task ---

修改一下`重複`{:class="block3control"}迴圈前面的`彈跳力`{:class="block3variables"}的值，這個變數是彈跳力預設的值，值愈大，表示跳的愈高。 修改完後就測試一下。

你可以任意的修改你想要的值，直到你滿意為止。

--- /task ---