# Model-Sizes-Plus
Updated, advanced, more precise version of the old modelsizes include.


## Generator
```pawn
new Line[2][1536], Float:oX, Float:oY, Float:oZ, Float:R, File:Sizes = fopen("sizes.txt", io_append), File:Offsets = fopen("offsets.txt", io_append);
	for(new row; row < 1000; row++) 
	{
		Line[0][0] = EOS; Line[1][0] = EOS;
		strcat(Line[0], "\t\t"); strcat(Line[1], "\t\t");
		for(new col; col < 20; col++)
		{
			new model = (row * 20) + col;
			CA_GetModelBoundingSphere(model, oX, oY, oZ, R);
			strcat(Line[0], sprintf("%s%0.6f,", R));
			strcat(Line[1], sprintf("{%0.6f, %0.6f, %0.6f}, ", oX, oY, oZ));
		}
		strcat(Line[0], "\r\n"); strcat(Line[1], "\r\n");
		fwrite(Sizes, Line[0]); fwrite(Offsets, Line[1]);
	}
	fclose(Sizes);
	fclose(Offsets);
```
