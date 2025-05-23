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
#export REGION=OBERFRANKEN

# define DEM paths
export DEM_SONN1=srtm/dem/hgt/SONN1
export DEM_SRTM1=srtm/dem/hgt/SRTM1v3.0
export DEM_ALOS1=srtm/dem/hgt/ALOS1.hgt

export TYP=fenix-cyclosm.TYP
export STYLE=fzk-fenix-cyclosm 

# some build par
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
./mt.pl --ram=$RAM --cores=$CORES --language=de --typfile=$TYP --style=$STYLE build Freizeitkarte_$REGION DWINTERSPORT DEXTENDEDROUTING DT36ROUTING DKULTURLAND DTRIGMARK

# build different map types
# Fenix
./mt.pl --ram=$RAM --cores=$CORES --language=de --typfile=$TYP --style=$STYLE --dempath=${DEM_SONN1} --demtype=1 gmapsupp Freizeitkarte_$REGION
mv install/Freizeitkarte_${REGION}_de/gmapsupp.img install/Freizeitkarte_${REGION}_de/Freizeitkarte_$REGION.img
# BaseCamp
./mt.pl --ram=$RAM --cores=$CORES --language=de --typfile=$TYP --style=$STYLE --dempath=${DEM_SONN1} --demtype=1 gmap Freizeitkarte_$REGION
