gdalbuildvrt -vrtnodata 0 dtm-2014.vrt *.tif

CREATE SCHEMA IF NOT EXISTS agi_lidar_2014;

raster2pgsql -d -s 2056 -l 16 -I -C -M -F -r *.tif -t 100x100 agi_lidar_2014.dtm | psql -d sogis -U ddluser -W -h 127.0.0.1

CREATE INDEX
ANALYZE
CREATE INDEX
ANALYZE
NOTICE:  Adding SRID constraint
NOTICE:  Adding scale-X constraint
NOTICE:  Adding scale-Y constraint
NOTICE:  Adding blocksize-X constraint
NOTICE:  Adding blocksize-Y constraint
NOTICE:  Adding alignment constraint
NOTICE:  Adding coverage tile constraint required for regular blocking
NOTICE:  Unable to create coverage raster. Cannot add coverage tile constraint: rt_raster_new: Dimensions requested exceed the maximum (65535 x 65535) permitted for a raster (XX000)
WARNING:  Unable to add constraint: 'regular_blocking'.  Skipping
NOTICE:  Adding number of bands constraint
NOTICE:  Adding pixel type constraint
NOTICE:  Adding nodata value constraint
NOTICE:  Adding out-of-database constraint
NOTICE:  Adding maximum extent constraint
 addrasterconstraints
----------------------
 t
(1 row)

NOTICE:  Adding SRID constraint
NOTICE:  Adding scale-X constraint
NOTICE:  Adding scale-Y constraint
NOTICE:  Adding blocksize-X constraint
NOTICE:  Adding blocksize-Y constraint
NOTICE:  Adding alignment constraint
NOTICE:  Adding coverage tile constraint required for regular blocking
NOTICE:  Unable to create coverage raster. Cannot add coverage tile constraint: rt_raster_new: Dimensions requested exceed the maximum (65535 x 65535) permitted for a raster (XX000)
WARNING:  Unable to add constraint: 'regular_blocking'.  Skipping
NOTICE:  Adding number of bands constraint
NOTICE:  Adding pixel type constraint
NOTICE:  Adding nodata value constraint
NOTICE:  Adding out-of-database constraint
NOTICE:  Adding maximum extent constraint
 addrasterconstraints
----------------------
 t
(1 row)

NOTICE:  Adding SRID constraint
NOTICE:  Adding scale-X constraint
NOTICE:  Adding scale-Y constraint
NOTICE:  Adding blocksize-X constraint
NOTICE:  Adding blocksize-Y constraint
NOTICE:  Adding alignment constraint
NOTICE:  Adding coverage tile constraint required for regular blocking
NOTICE:  Raster is not aligned to tile grid of coverage
NOTICE:  Unable to add constraint: enforce_coverage_tile_rast
NOTICE:  SQL used for failed constraint: ALTER TABLE agi_lidar_2014.o_16_dtm ADD CONSTRAINT enforce_coverage_tile_rast CHECK (st_iscoveragetile(rast, '0100000000000000000000204000000000000020C00000000080C6434100000000B04133410000000000000000000000000000000008080000E119ED17'::raster, 100, 100))
NOTICE:  Returned error message: check constraint "enforce_coverage_tile_rast" is violated by some row (23514)
WARNING:  Unable to add constraint: 'regular_blocking'.  Skipping
NOTICE:  Adding number of bands constraint
NOTICE:  Adding pixel type constraint
NOTICE:  Adding nodata value constraint
NOTICE:  Adding out-of-database constraint
NOTICE:  Adding maximum extent constraint
----------------------
 t
(1 row)

 addoverviewconstraints
------------------------
 t
(1 row)

COMMIT
VACUUM
VACUUM