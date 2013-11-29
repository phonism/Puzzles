#**Chameleons**

###**Description**

On an island live 13 purple, 15 yellow and 17 maroon chameleons. When two chameleons of different colors meet, they both change into the third color. Is there a sequence of pairwise meetings after which all chameleons have the same color?

###**Solution**

It is not possible for all the chameleons to have the same color.

**Solution 1:** One way to start thinking about this puzzle is to notice that when a yellow ans blue chameleon meet and make two green chameleons, the numbers Y and B go down by 1, and the number G goes up by 2. In other words, the distance between G and either Y or B change by 3. In other words, the transformation has left unchanged the quantities

```
	mod(G - Y, 3)

	mod(G - B, 3)
```

Now let's remain focused on just these two special quantities, and consider whether the other two kinds of meetings could change them. If a green and a yellow chameleon meet, making a blue one, then we have

```
	mod((G - 1) - (Y - 1), 3) = mod(G - Y), 3)
    
	mod((G - 1) - (B + 2), 3) = mod(G - B - 3, 3) = mod(G - B, 3)
```

so no change occurs there, and you can convince yourself that no change occurs when a pair of yellow chameleons is created either.

Now, suppose that, by some series of meetings, we were able to make all the chameleons green. Then it would hava to be the case at this final state that the values of the two quantities would be

```
	mod(G - Y, 3) = mod(45 - 0, 3) = 0

	mod(G - B, 3) = mod(45 - 0, 3) = 0
```

But we started out with

```
	mod(17 - 17, 3) = mod(-2, 3) = 1
	
	mod(15 - 13, 3) = mod(2, 3) = 2
```

and from what we said, neither of these numbers can ever change. Therefore, from the given initial setup, we cannot end up with all green chameleons. It turns out that similar arguments show that we can't get all yellow, nor all blue chameleons.

**Solution 2:** Let \<p, y, m\> denote a population of p purple, y yellow and m maroon chameleons. Can population \<13, 15, 17\> can be transformed into \<45, 0, 0\>, or \<0, 45, 9\> or \<0, 0, 45\> through a series of pairwise meetings? Define function X(p, y, m) = (0p + 1y + 2m) mod 3. An interesting property of X is that its value does not change after any pairwise meeting because X(p, y, m) = X(p-1, y-1, m+2) = X(p-1, y+2, m-1) = X(p+2, y-1, m-1). Now X(13, 15, 17) equals 1. However, X(45, 0, 0) = X(0, 45, 0) = X(0, 0, 45) = 0**. This means that there is no sequence of pairwise meetings after which all chameleons will have identical color