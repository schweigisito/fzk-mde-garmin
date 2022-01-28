# Command to build maps

$ export REGION=OBERFRANKEN; ./mt.pl create Freizeitkarte_$REGION; ./mt.pl --downloadbar fetch_osm Freizeitkarte_$REGION; ./mt.pl --downloadbar fetch_ele --ele=10 Freizeitkarte_$REGION; ./mt.pl --ram=4096 --cores=2 join Freizeitkarte_$REGION; ./mt.pl --ram=4096 --cores=2 --language=de split Freizeitkarte_$REGION; ./mt.pl --ram=4096 --cores=2 --typfile=fenix-schweigi.TYP --style=fzk-fenix-schweigi --language=de build Freizeitkarte_$REGION DWINTERSPORT DEXTENDEDROUTING DT36ROUTING; ./mt.pl --ram=4096 --cores=2 --typfile=fenix-schweigi.TYP --style=fzk-fenix-schweigi --language=de gmapsupp Freizeitkarte_$REGION



