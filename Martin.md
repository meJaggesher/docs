## $Martin- On Fly GEO JSON to PBF$

Repo Link: [https://github.com/urbica/martin](https://github.com/urbica/martin)

```bash
martin postgres://uName:pass@10.10.3.161:5432/osmbd
```

```bash
martin --listen-addresses=localhost:4001 postgres://uName:pass@10.10.3.161:5432/osmbd
```

```js
map.addLayer({
  id: 'public.points',
  type: 'circle',
  source: {
    type: 'vector',
    url: 'http://localhost:3000/public.points.json'
  },
  'source-layer': 'public.points'
});
```

```yaml
---
# Database connection string
connection_string: "postgres://Uname:Pass@10.10.3.161:5432/osmbd"

# Connection keep alive timeout [default: 75]
keep_alive: 75

# The socket address to bind [default: 0.0.0.0:3000]
listen_addresses: "0.0.0.0:4000"

# Maximum connections pool size [default: 20]
pool_size: 20

# Enable watch mode
watch: false

# Number of web server workers
worker_processes: 8

# associative arrays of table sources
table_sources:
  public.table_source:
    # table source id
    id: public.table_source
    # table schema
    schema: public
    # table name
    table: table_source
    # geometry column name
    geometry_column: geom
    # geometry srid
    srid: 4326
    # tile extent in tile coordinate space
    extent: 4096
    # buffer distance in tile coordinate space to optionally clip geometries
    buffer: 64
    # boolean to control if geometries should be clipped or encoded as is
    clip_geom: true
    # geometry type
    geometry_type: GEOMETRY
    # list of columns, that should be encoded as tile properties
    properties:
      gid: int4

  public.planet_osm_point:
    # table source id
    id: public.planet_osm_point
    # table schema
    schema: public
    # table name
    table: planet_osm_point
    # geometry column name
    geometry_column: way
    # geometry srid
    srid: 4326
    # tile extent in tile coordinate space
    extent: 4096
    # buffer distance in tile coordinate space to optionally clip geometries
    buffer: 64
    # boolean to control if geometries should be clipped or encoded as is
    clip_geom: true
    # geometry type
    geometry_type: GEOMETRY
    # list of columns, that should be encoded as tile properties
    properties:
      osm_id: int8
```
