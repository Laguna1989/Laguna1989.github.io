# Laguna1989.github.io
heatguide techdemo

// create 
for (i in 0...Tile.WorldSize)
{
	for (j in 0...Tile.WorldSize)
	{
		var t: Tile = new Tile(i, j);
		var x : Float = i * dx;
		var y : Float = j * dx;
		t.Temperatur = 1- ((x - Tile.WorldSize/4.0)*(x - Tile.WorldSize/4.0)*sigma +  (y - Tile.WorldSize/4.0)*(y - Tile.WorldSize/4.0)*sigma);
	}
}

// update
for ( i in 1 ... Tile.WorldSize-1 )
{
  for ( j in 1 ... Tile.WorldSize-1 )
  {
	  var t : Tile = GetTile(i, j);
    var v = t.Temperatur +    // this tiles Temperatre
  	  0.1 * ( 
  	  GetTile(i + 1, j).Temperatur + GetTile(i - 1,j).Temperatur +  // neighbours
  	  GetTile(i, j - 1).Temperatur + GetTile(i, j + 1).Temperatur - 
  	  4.0 * t.Temperatur ); // again this tile

    t.Temperatur = v ;
     }
 }
