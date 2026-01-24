---
date created: Thursday, January 15th 2026, 4:18:05 pm
date modified: Saturday, January 24th 2026, 6:34:46 pm
---

# Preface:

European players tend to struggle with riichi mahjong for as the majority of learning resources are for Japanese audiences. Hence, most European players are not playing at a sophisticated standard.

Riichi Book 1 attempts to remedy this - it is designed for players who are below the rank of 四段 (`Yondan/4th-Dan`, or Expert Mahjong Soul). Whereas Riichi Book 2 is for advanced players who are below 七段 (`Shichidan/7th-Dan` or Saint Mahjong Soul).

## Plan of the Book:

A balance between theoretical study, and practical play is the best approach to improving at mahjong. Learn chunks, then apply them to a game under real-time pressure and come back for more.

## Rankings:
### `一般/ippan` Lower-level Room (Novice-Adept):

The `ippan` (Bronze/Silver Room) is where players typically start out. Games can be chaotic and random, the rules are not very well understood and big mistakes are made regularly.
### `上級/joukyu` Upper-level Room (Expert-Master):

The `joukyu` (Gold/Low Jade Room) is where most players who have a solid grasp of the game lie, the quality of play is much more normal, but there is still many players who lack defence, do meaningless `dama` and poor `riichi`, and make serious mistakes relating to tile efficiency.

Most European players and tournaments operate at this level or the `ippan` level.
### `特上/tokujou` Advanced Room (Saint 1-2):

The `tokujou` (High Jade/Low Throne Room) is where intermediate players transform into advanced players, there are fewer fundamental errors, but defensive reading and situational judgment are still developing and games are similar to that of the `フリー/furii` mahjong parlours in Japan.
### `鳳凰/houou` Phoenix Room (Saint 3/Celestial):

The `houou` (High Throne Room) is where the best mahjong players in the world play. Whilst you may see a `houou` level player in a mahjong parlour, you don't normally play a game with four of them at once.

Mistake making is minimal and play approaches the professional standards of mahjong leagues, minus tournament pressure. The mental game becomes more important here.

## Reading Statistics:

### Placement Rates:

Ideally you want your placement rates to be a positive slope. You achieve first more than 2nd, 2nd more than 3rd, and so on. But you want your average placement to be **<2.5** which would state you are winning more than losing. 

Placement rate only matters of over the course of a large enough sample size. (e.g. 100 games or so). You can calculate your average from percentages like so:

```Maths
(1 × 0.2791) + (2 × 0.3140) + (3 × 0.1977) + (4 × 0.2093) = 2.32
```
## Hand Statistics:

### `和了率/Agaritsu` Hand Win Rate :

`Agaritsu` is a measure of how many hands you win. Statistically you should have a 25% win rate of hands, so any win rate above 25% is strong.

Though win rate percentage depends on other factors:

- A lower deal-in rate but lower hand win rate is fine.
- Building big hands but having a lower win rate is fine.
	- Hand win rate should be consider along with hand-value and timing.
	- Winning 23% of hands with big hands is worth more than 28% winrate with cheap hands

### `放銃率/Houjuritsu` Deal-in Rate:

`Houjuritsu` is a measure of how many hands you got `Ronned` or fed your opponent the winning tile. You want to keep this down.

There are a few times where the best play would increase this:

1. You deal-off an opponent to secure your placement.
2. You discard dangerous tiles to secure your chance of winning a hand/securing a big hand.
	1. As this would increase your win-rate over time, even if you deal-in more.

The rule of thumb is that if you have a high deal-in rate, you need to win more, but if you have a low deal in rate you can win less. In other words:

```Maths
(Win rate - Deal-in rate) = 10% point gap. e.g.
27.77% - 14.67% = 13.1% (Good)
27.77% - 20% = 7.77% (Bad)
```

Your deal-in rate matters more as you climb up further, because the penalties for 4th place also rise. 
### `副露率/fukuroritsu` Call Rate:

`Fukuroritsu` is a measure of how many hands you play open `(chii/pon/kan)`. It measures your preference for open or closed hands. The basic idea, is don't open hands unless it secures a yaku.

Generally speaking as players improve, they call slightly more because they understand when to call or when to play fast.

### `立直率/tachinaoritsu` Riichi Rate:

`tachinaoritsu` is a measure of the hands which you call `riichi`. It measures your strategic approach to mahjong. 

Generally speaking, riichi rate tends to go down slightly as players improve, since they call more often or go into `dama` and thus can't riichi.

***
# Basic Tile Efficiency:

## Learning Strategies:

Mahjong is governed by luck in the short-term, but skill and strategy in the long-term. Unskilled players can crush strong players, but learning strategy principles is critical in the long-run.

Furthermore, you can enjoy the game at a deeper level once you understand principles.

Mahjong is probabilistic - meaning that making the best choice doesn't always lead to the best outcome. The best choices are those that lead to the best outcome - **on average.** 

An analysis of hands or decision making needs to consider a statistical assessment of possible results. 

For example (assuming no dead tiles):
![[Pictures/Pasted image 20260117130058.png]]

1. Discard the `6-pinzu` -> `6-7p shape` waiting on `5p/8p` (`Ryanmen Wait`)
	1. Waiting for 8 tiles.
2. Discard the `7-pinzu` -> `4m6p shanpon` waiting on `4m/6p` (`Shanpon Wait`)
	1. Waiting for 4 tiles (Since we already have two `4m` and `6p`).

Our `Ryanmen Wait` is stronger than the `Shanpon Wait` as we have a higher acceptance rate and are more likely to complete our hand.

It is possible that you go with the superior `Ryanmen Wait`, and your opponents never discard any `5p or 8p` and discard `4m or 6p`. You haven't made a bad decision, but you simply were unlucky. Keep calm and carry on.

Thus, tile efficiency is about **improving** your chances of winning, not guaranteeing wins. There are little guarantees in mahjong.
## Basic Building Blocks:

### Number Tiles:

The number tiles are the most abundant tiles in the wall, they constitute 108 of the 136 tiles.

![[Pictures/Pasted image 20260117132006.png]]

Number tiles are broken down further into **simples** (`tanyao hai (2 to 8)`) and **terminals** (`yaochu hai (1 and 9)`) tiles. This is because they generate different `yaku` and different values of `fu (mini-points)`.

Most modern riichi games use the `aka dora (red 5m/5p/5s)` these tiles are treated as `dora` tiles no matter the `dora` indicator. Interestingly, when a 4 is the dora indicator, these red fives are worth a **double dora!** 

### Honour Tiles:

The honour tiles are more rare, they constitute 28 of the 136 tiles.

![[Pictures/Pasted image 20260117134141.png]]

Some honour tiles are **value tiles** (`yakuhai`) we gain one `han` **if we collect a triplet**. For reference:

- Dragon tiles are always a `yakuhai`
- Wind tiles are a `yakuhai`, if:
	- Your seat corresponds to the tile. (`Pei in the north seat -> 1 han`)
	- The round corresponds to the tile. (`Ton in the north seat, during east 3 round -> 1 han`)
	- If both your seat and round wind match, you gain **2 yaku!** (`Ton in the east seat, during east 3 round -> 2 han`)

You do have valueless wind tiles (`3 Sha as the north player -> 0 han`), as it is valuable to the west player, but valueless to other players at the table (`otakaze`).
#### Honour Tiles as Dora Indicators:

It is important to be careful about the dora if the indicator is an honour tile. as the amount of `han` can really add up.

The `dora indicator` for the honour tiles are the following:
![[Pictures/Pasted image 20260117140450.png]]

For example: `East seat on East 3, pei is dora indicator, triplet of ton -> 5 han!`
### Groups:

The main goal of a mahjong hand is to win a hand (or avoid dealing-in to another player). To build a winning hand, we need to complete four groups (`mentsu`) and one head/eyes (`atama`). 

There are exceptions to this: `Chiitoistu`/ Seven pairs, `Kokushi Musuo`/ Thirteen Orphans, and `Nagashi Mangan`/ All Terminals and Honours Discard do not follow these rules.

Groups are classified as **runs** or **sets.**
1. Run (`shuntsu`/ sequence) is a set of three consecutive number tiles.
2. Set (`kotsu` / triplet ) is a set of three identical tiles. 

### Ready and `n-away`:

We say that a hand is ready (`tenpai`) when the hand is one tile away from completion. 

For example:
![[Pictures/Pasted image 20260118150530.png]]

We can say that a hand becomes 1-away from ready (`1-shanten/Iishanten`), when we reach tenpai with one more tile.

For example:
![[Pictures/Pasted image 20260118151046.png]]

We can say a hand is 2-away from ready (`2-shanten/Ryanshanten`) when we would reach tenpai with two more tiles.

For example:
![[Pictures/Pasted image 20260118151456.png]]

**Tile acceptance** (`ukeire`) refers to the kinds and numbers of tiles that a hand accepts. If hands are in equal positions of `shanten`, the hand with the wider tile acceptance is better than one with a tighter range.

Practically speaking, we don't need to recognise hands that are 3-away or worse. But we do care about recognising hands that are: `Tenpai`, `Iishanten`, `Ryanshanten`, and `Sanshanten`. As they enable us to construct better winning hands, through knowledge of tile acceptance (`ukeire`).

| **Shanten Level** | **Japanese** | **Pronunciation**                 |
| ----------------- | ------------ | --------------------------------- |
| **0-shanten**     | **聴牌**       | **Tenpai** (pronounced _ten-pie_) |
| **1-shanten**     | **一向聴**      | **Iishanten** (_ee-shan-ten_)     |
| **2-shanten**     | **二向聴**      | **Ryanshanten** (_ryan-shan-ten_) |
| **3-shanten**     | **三向聴**      | **Sanshanten** (_san-shan-ten_)   |
| **4-shanten**     | **四向聴**      | **Suushanten** (_soo-shan-ten_)   |
| **5-shanten**     | **五向聴**      | **Uushanten** (_oo-shan-ten_)     |
| **6-shanten**     | **六向聴**      | **Ryoushanten** (_ryo-shan-ten_)  |
#### Tile Acceptance Shrinkage:

As we get closer to `Tenpai` the number of tiles we can accept gets smaller and smaller.

If we consider the earlier hands for example:
![[Pictures/Pasted image 20260118151913.png]]

Tile acceptance is minimized when the hand is in `Tenpai`, but you are able to either `Tsumo` or `Ron` into winning tiles whilst in `Tenpai`. 

With `Iishanten/Ryanshanten` you are mostly dependant* on the tiles that you draw to advance your hand. For this reason, when we transition from `Ryanshanten`-> `Iishanten` we don't want to decrease our tile acceptance too much.

_Melding (`Pon/Chii`) can be used to speed up your hand, but it has a few problems:_
1. _Your hand loses value or can lose `yaku`._
	1. _This can be fine if you are looking to avoid exhaustive draw or want a fast hand._
2. _You sometimes won't be able to meld as your tile structure wouldn't permit it._
	1. _e.g. In our `Ryanshanten` example, we could accept the `3s`, yet it is already in a run and we have no pair. Thus, `Pon/Chii` cannot be called._

#### Advancing Your Hand:

To win a hand we need to move from the later stages of `shanten` and creep closer to `tenpai`. 

For example:
![[Pictures/Pasted image 20260120123718.png]]

Discarding the `9s` makes the hand `Ryanshanten`, whilst discarding the `7m or 4s` makes the hand `Iishanten`. Hence, we want to enter `Iishanten`, this can change if we enter `tenpai` with fewer than 2 kinds of tiles to accept.

In this example though, discarding the `7m/4s` we wait on `2p, 5p, 8s` (3 kinds with 12 tiles).

### Protoruns (`Taatsu`):

It is much easier to finish a hand using a run rather than a triplet. As you have more tiles worth of acceptance that you can wait for, rather than looking for 3 out of 4 identical tiles.

We call pairs of tiles that can complete a run a `protoun/taatsu`, we can define the basic protoruns, as `ryanmen waits/shapes, kanchan waits/shapes, penchan waits/shapes`

For example:
![[Pictures/Pasted image 20260120142844.png]]

Out of these protoruns, the `ryanmen` is the strongest as it accepts double the amount of tiles, so building these ryanmen shapes helps us progress our hand more often than not.

### Closed Wait VS Edge Wait (`Kanchan` Vs `Penchan`):

We prefer closed (`kanchan`) waits over edge (`penchan`) waits. Why? Because the closed wait can be converted into a `ryanmen` more easily.

For example - A `13p kanchan`:
![[Pictures/Pasted image 20260120143216.png]]

We draw a `4p` and we discard the `1p` convert into a `ryanmen`, which is a more efficient shape.

For example - A `89p penchan`:
![[Pictures/Pasted image 20260120143912.png]]

It takes two steps, `89p -> 68p -> 56p` to convert into a `ryanmen`. This is slower than the `kanchan` shape. So if we have a decision between breaking a `kanchan` or `penchan` we should break the `penchan` for pure tile efficiency.

**Hence:**
> **Side Wait (`Ryanmen`) > Closed Wait (`Kanchan`) > Edge Wait (`Penchan`)**
### Tile Versatility:

Some tiles are more versatile than others, number tiles are better than honour tiles, since honour tiles can't form sequences. Also, the type or number of `taatsu/protoruns` that can be made also influences how useful tiles are.

For this reason, the following rules apply:
- Number tiles 3-7 are most versatile, as they form `taatsu` with four tiles.
	- `3p` can form two `ryanmen` shapes (`23p + 34p`) and two `kanchan` shapes (`13p + 35p`)
- Number tiles 2-8 are less versatile, as the form `taatsu` with three tiles.
	- `2p` can form one `ryanmen` shape (`23p`) and one `kanchan` shape (`24p`) and one penchan shape (`12p`)
- Terminal tiles `(1 and 9)` are least versatile, as they form `taatsu` with only two tiles.
	- `1p` can form one `kanchan` shape (`13p`) and one `penchan` shape (`12p`).

**Hence:**
> **3-7 tiles > 2, 8 tiles > 1,9 tiles > honour tiles** (When considering purely `ukerie/tile effeciency`)


### `Kanchan/Closed Wait` Versatility:

Using the same logic as within [[#Tile Versatility]] we can order the versatility of `kachan` protoruns.





