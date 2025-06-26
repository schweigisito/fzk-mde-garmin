# commands to build garmin maps
#
# call it via
#
# $ bash < BUILD

#export REGION=BAYERN
#export REGION=ALPS
#export REGION=HRV # Kroatien
#export REGION=SVN # Slowenien
#export REGION=NOR
#export REGION=ESP
#export REGION=DEU
export REGION=OBERFRANKEN
#export REGION=BEL
#export REGION=FRA
#export REGION=DNK

# define DEM paths
export DEM=srtm/dem/hgt/sonnyy7

# define TYP file
export TYP=fenix-cyclosm.TYP

# define STYLE file
export STYLE=fzk-fenix-cyclosm 

# some build parameter
export CORES=8
export RAM=60000

# fetch boundaries and sea boundaries
#./mt.pl bootstrap

# fetch OSM and ELE data
./mt.pl create Freizeitkarte_$REGION
./mt.pl --downloadbar fetch_osm Freizeitkarte_$REGION
./mt.pl --downloadbar fetch_ele --ele=10 Freizeitkarte_$REGION

./mt.pl --ram=$RAM --cores=$CORES join Freizeitkarte_$REGION
./mt.pl --ram=$RAM --cores=$CORES --language=de split Freizeitkarte_$REGION

# build
./mt.pl --ram=$RAM --cores=$CORES --language=de --typfile=$TYP --style=$STYLE --dempath=${DEM} --demtype=1 build Freizeitkarte_$REGION DWINTERSPORT DEXTENDEDROUTING DT36ROUTING DTRIGMARK

# GPS Receiver
./mt.pl --ram=$RAM --cores=$CORES --language=de --typfile=$TYP --style=$STYLE --dempath=${DEM} --demtype=1 gmap Freizeitkarte_$REGION DWINTERSPORT DEXTENDEDROUTING DT36ROUTING DTRIGMARK

# BaseCamp
./mt.pl --ram=$RAM --cores=$CORES --language=de --typfile=$TYP --style=$STYLE --dempath=${DEM} --demtype=1 gmapsupp Freizeitkarte_$REGION DWINTERSPORT DEXTENDEDROUTING DT36ROUTING DTRIGMARK

# rename GPS Receiver map
mv install/Freizeitkarte_${REGION}_de/gmapsupp.img install/Freizeitkarte_${REGION}_de/Freizeitkarte_$REGION.img
