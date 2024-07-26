# commands to build garmin maps
#
# call it via
#
# $ bash < BUILD

export REGION=BAYERN
#export REGION=ALPS
#export REGION=NOR
#export REGION=ESP
#export REGION=DEU

export CORES=8
export RAM=49152
./mt.pl create Freizeitkarte_$REGION
./mt.pl --downloadbar fetch_osm Freizeitkarte_$REGION
./mt.pl --downloadbar fetch_ele --ele=10 Freizeitkarte_$REGION
./mt.pl --ram=$RAM --cores=$CORES join Freizeitkarte_$REGION
./mt.pl --ram=$RAM --cores=$CORES --language=de split Freizeitkarte_$REGION
./mt.pl --ram=$RAM --cores=$CORES --typfile=fenix-cyclosm.TYP --style=fzk-fenix-cyclosm --language=de build Freizeitkarte_$REGION DWINTERSPORT DEXTENDEDROUTING DT36ROUTING
./mt.pl --ram=$RAM --cores=$CORES --typfile=fenix-cyclosm.TYP --style=fzk-fenix-cyclosm --language=de gmapsupp Freizeitkarte_$REGION
mv install/Freizeitkarte_${REGION}_de/gmapsupp.img install/Freizeitkarte_${REGION}_de/freizeitkarte_$REGION.img
./mt.pl --ram=$RAM --cores=$CORES --typfile=fenix-cyclosm.TYP --style=fzk-fenix-cyclosm --language=de gmap Freizeitkarte_$REGION
