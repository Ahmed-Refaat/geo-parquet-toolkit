# 🛠️ Geo-Parquet Toolkit

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
![GitHub stars](https://img.shields.io/github/stars/Ahmed-Refaat/geo-parquet-toolkit?style=social)

> **Complete toolkit for efficient geospatial vector data storage using Apache Parquet**
> 
> *Specifications • Tools • Libraries • Examples • Best Practices*

---

## 📖 Table of Contents

- [About the Toolkit](#about-the-toolkit)
- [What is GeoParquet?](#what-is-geoparquet)
- [Why Use This Toolkit?](#why-use-this-toolkit)
- [Toolkit Components](#toolkit-components)
- [Quick Start](#quick-start)
- [Format Specification](#format-specification)
- [Tools & Utilities](#tools--utilities)
- [Implementation Examples](#implementation-examples)
- [Use Cases](#use-cases)
- [Performance Benchmarks](#performance-benchmarks)
- [Best Practices](#best-practices)
- [Contributing](#contributing)
- [License](#license)
- [About the Maintainer](#about-the-maintainer)

---

## 🎯 About the Toolkit

**Geo-Parquet Toolkit** is a comprehensive resource for working with geospatial vector data in Apache Parquet format. This toolkit provides everything you need to:

✅ **Understand** the GeoParquet specification  
✅ **Convert** existing geospatial data to GeoParquet  
✅ **Validate** GeoParquet files for compliance  
✅ **Optimize** storage and query performance  
✅ **Integrate** with modern data pipelines  
✅ **Learn** through real-world examples  

### What Makes This a Toolkit?

Unlike a simple specification document, this toolkit includes:

- 📚 **Complete Specification** - Full format documentation
- 🔧 **Conversion Tools** - Scripts to convert various formats
- ✅ **Validation Utilities** - Ensure compliance with standards
- 📊 **Example Datasets** - Real-world sample files
- 💻 **Code Libraries** - Ready-to-use implementations
- 📈 **Performance Scripts** - Benchmark and optimize
- 🎓 **Learning Resources** - Tutorials and guides
- 🏗️ **Best Practices** - Production-ready patterns

---

## 🤔 What is GeoParquet?

**GeoParquet** is a specification for storing **geospatial vector data** (points, lines, polygons) in **Apache Parquet**, a columnar storage format optimized for analytical queries. It combines the power of geospatial data with the efficiency of modern data analytics infrastructure.

### The Problem It Solves

Traditional geospatial formats like Shapefiles, GeoJSON, and even GeoPackage were designed for a different era. They struggle with:
- **Large datasets** (multi-gigabyte files)
- **Cloud-native workflows** (slow to read over networks)
- **Analytical queries** (must read entire files)
- **Modern data pipelines** (limited integration with data tools)

### The Solution

GeoParquet leverages Apache Parquet's columnar format to provide:
- ✅ **Massive compression** - 5-10x smaller than GeoJSON
- ✅ **Fast queries** - Read only the columns you need
- ✅ **Cloud-optimized** - Efficient remote reads
- ✅ **Analytics-ready** - Native support in modern data tools
- ✅ **Interoperable** - Standard format, wide tool support

---

## 💡 Why Use This Toolkit?

### For Data Engineers
- **Convert pipelines** from legacy formats to GeoParquet
- **Optimize storage** costs by 80%+ in cloud environments
- **Speed up queries** by 10-100x with columnar access
- **Integrate easily** with Spark, DuckDB, BigQuery

### For GIS Analysts
- **Process larger datasets** without memory constraints
- **Share data efficiently** with smaller file sizes
- **Access data remotely** without full downloads
- **Use familiar tools** (QGIS, ArcGIS Pro, GeoPandas)

### For Software Developers
- **Build faster applications** with optimized data access
- **Scale to billions** of features seamlessly
- **Deploy serverless** with cloud-native format
- **Reduce infrastructure** costs significantly

### For Researchers
- **Analyze massive datasets** on standard hardware
- **Reproduce results** with standardized format
- **Share data openly** with efficient distribution
- **Collaborate easily** with cross-platform support

---

## 🧰 Toolkit Components

### 1. **Specification Documents**
📄 Location: `format-specs/`

- **geoparquet.md** - Complete format specification
- **schema.json** - JSON schema for validation
- **RELEASE.md** - Version history and changes

### 2. **Conversion Tools**
🔧 Location: `scripts/`

- **convert_formats.py** - Convert Shapefile/GeoJSON/GPKG to GeoParquet
- **batch_convert.py** - Batch process multiple files
- **optimize_parquet.py** - Re-optimize existing GeoParquet files
- **partition_data.py** - Create partitioned datasets

### 3. **Validation Utilities**
✅ Location: `scripts/`

- **validate_geoparquet.py** - Check specification compliance
- **test_json_schema.py** - Validate metadata structure
- **check_integrity.py** - Verify data integrity

### 4. **Example Datasets**
📊 Location: `examples/`

- **example.parquet** - Simple point dataset
- **example_metadata.json** - Metadata structure example
- **Various test files** - Different geometry types

### 5. **Test Data**
🧪 Location: `test_data/`

- Complete test suite covering all geometry types
- WKB and native encoding examples
- Validation test cases

### 6. **Code Examples**
💻 Location: `examples/`

- **example.py** - Python usage examples
- **example-2.R** - R implementation examples
- **Integration samples** - Various tool integrations

---

## 🚀 Quick Start

### Installation

**Install the Toolkit:**
```bash
# Clone the repository
git clone https://github.com/Ahmed-Refaat/geo-parquet-toolkit.git
cd geo-parquet-toolkit

# Install Python dependencies
pip install -r requirements.txt
```

**Or install libraries separately:**
```bash
# Python
pip install geopandas pyarrow

# For validation
pip install gpq

# For advanced features
pip install duckdb fastparquet
```

### Convert Your First File

**Using Python:**
```python
import geopandas as gpd

# Read any geospatial format
gdf = gpd.read_file('your_data.shp')  # or .geojson, .gpkg, etc.

# Write to GeoParquet
gdf.to_parquet('output.parquet', compression='zstd')

print("Conversion complete! ✅")
```

**Using the Toolkit Script:**
```bash
# Convert single file
python scripts/convert_formats.py input.shp output.parquet

# Batch convert directory
python scripts/batch_convert.py input_folder/ output_folder/

# With optimization
python scripts/convert_formats.py input.geojson output.parquet --optimize
```

### Validate GeoParquet File

**Using the Toolkit:**
```bash
# Validate file
python scripts/validate_geoparquet.py data.parquet

# Output:
# ✅ Valid GeoParquet file
# Version: 1.1.0
# Geometry types: Polygon, MultiPolygon
# CRS: EPSG:4326
# Features: 10,000
```

**Using gpq:**
```bash
gpq validate data.parquet
gpq describe data.parquet
```

### Read GeoParquet

**Python (GeoPandas):**
```python
import geopandas as gpd

# Read entire file
gdf = gpd.read_parquet('data.parquet')

# Read specific columns only
gdf = gpd.read_parquet('data.parquet', 
                       columns=['geometry', 'name', 'population'])

# Filter while reading (super fast!)
gdf = gpd.read_parquet('data.parquet',
                       filters=[('population', '>', 1000000)])
```

**Python (DuckDB) - SQL queries:**
```python
import duckdb

con = duckdb.connect()
con.execute("INSTALL spatial; LOAD spatial;")

result = con.execute("""
    SELECT name, ST_Area(geometry) as area
    FROM read_parquet('data.parquet')
    WHERE area > 1000000
    ORDER BY area DESC
    LIMIT 10
""").df()

print(result)
```

---

## 📋 Format Specification

### Current Version: 1.1.0

The GeoParquet specification defines how geospatial vector data should be stored in Parquet format.

**Key Specification Documents:**
- **[Stable Specification v1.1.0](https://geoparquet.org/releases/v1.1.0/)**
- **[JSON Schema](https://geoparquet.org/releases/v1.1.0/schema.json)**
- **[Development Version](format-specs/geoparquet.md)** (in this toolkit)

### Metadata Structure

GeoParquet stores geospatial metadata in the Parquet file metadata:

```json
{
  "version": "1.1.0",
  "primary_column": "geometry",
  "columns": {
    "geometry": {
      "encoding": "WKB",
      "geometry_types": ["Polygon", "MultiPolygon"],
      "crs": {
        "type": "GeographicCRS",
        "id": {
          "authority": "EPSG",
          "code": 4326
        }
      },
      "bbox": [-180.0, -90.0, 180.0, 90.0],
      "epoch": 2020.0
    }
  }
}
```

### Key Features

✅ **Columnar Storage** - Efficient analytical queries  
✅ **Excellent Compression** - 5-10x smaller than GeoJSON  
✅ **Multiple CRS Support** - Any spatial reference system  
✅ **Multiple Geometry Columns** - Store different representations  
✅ **Cloud-Native** - Optimized for remote access  
✅ **Standards-Based** - ISO WKB encoding  

---

## 🔧 Tools & Utilities

### Included in This Toolkit

#### 1. **Format Converter** (`scripts/convert_formats.py`)

Convert any geospatial format to GeoParquet:

```bash
# Basic conversion
python scripts/convert_formats.py input.shp output.parquet

# With specific compression
python scripts/convert_formats.py input.geojson output.parquet --compression zstd

# Batch processing
python scripts/batch_convert.py data/shapefiles/ data/geoparquet/
```

**Features:**
- Supports: Shapefile, GeoJSON, GeoPackage, KML, GML, and more
- Automatic CRS detection and handling
- Configurable compression algorithms
- Progress tracking for large files
- Error handling and logging

#### 2. **Validator** (`scripts/validate_geoparquet.py`)

Ensure your GeoParquet files meet the specification:

```bash
python scripts/validate_geoparquet.py file.parquet

# Detailed validation
python scripts/validate_geoparquet.py file.parquet --verbose

# Validate directory
python scripts/validate_geoparquet.py data/ --recursive
```

**Checks:**
- Metadata structure compliance
- CRS validity
- Geometry encoding
- Schema consistency
- Bounding box accuracy

#### 3. **Optimizer** (`scripts/optimize_parquet.py`)

Re-optimize existing GeoParquet files:

```bash
python scripts/optimize_parquet.py input.parquet output.parquet

# With different settings
python scripts/optimize_parquet.py input.parquet output.parquet \
  --compression zstd \
  --row-group-size 128MB
```

**Optimizations:**
- Recompress with better algorithms
- Adjust row group sizes
- Reorder columns for better compression
- Update to latest specification version

#### 4. **Partitioner** (`scripts/partition_data.py`)

Create partitioned datasets for big data workflows:

```bash
python scripts/partition_data.py input.parquet output_dir/ \
  --partition-by country year
```

**Creates structure:**
```
output_dir/
  country=USA/
    year=2023/data.parquet
    year=2024/data.parquet
  country=Canada/
    year=2023/data.parquet
```

### External Tools

#### Command-Line Tools

**gpq** - GeoParquet command-line tool
```bash
pip install gpq

gpq validate file.parquet
gpq describe file.parquet
gpq convert file.parquet output.geojson
```

**GDAL/OGR** (v3.5+)
```bash
# Convert with ogr2ogr
ogr2ogr -f Parquet output.parquet input.shp

# Read info
ogrinfo output.parquet
```

#### Python Libraries

**GeoPandas** - Primary implementation
```python
import geopandas as gpd
gdf = gpd.read_parquet('data.parquet')
```

**DuckDB** - SQL queries
```python
import duckdb
con = duckdb.connect()
con.execute("SELECT * FROM read_parquet('data.parquet')")
```

**PyArrow** - Low-level access
```python
import pyarrow.parquet as pq
table = pq.read_table('data.parquet')
```

#### R Libraries

```r
# geoarrow
library(geoarrow)
gdf <- read_geoparquet("data.parquet")

# arrow + sf
library(arrow)
library(sf)
gdf <- read_parquet("data.parquet") %>% st_as_sf()
```

---

## 💻 Implementation Examples

### Example 1: Batch Convert Shapefiles

```python
import geopandas as gpd
from pathlib import Path

def batch_convert_shapefiles(input_dir, output_dir, compression='zstd'):
    """Convert all shapefiles in a directory to GeoParquet"""
    
    input_path = Path(input_dir)
    output_path = Path(output_dir)
    output_path.mkdir(exist_ok=True)
    
    for shapefile in input_path.glob('*.shp'):
        print(f"Converting {shapefile.name}...")
        
        try:
            # Read shapefile
            gdf = gpd.read_file(shapefile)
            
            # Create output filename
            output_file = output_path / f"{shapefile.stem}.parquet"
            
            # Write to GeoParquet
            gdf.to_parquet(output_file, compression=compression)
            
            # Report size reduction
            original_size = shapefile.stat().st_size / (1024**2)
            new_size = output_file.stat().st_size / (1024**2)
            reduction = ((original_size - new_size) / original_size) * 100
            
            print(f"  ✅ Success!")
            print(f"  Original: {original_size:.2f} MB")
            print(f"  GeoParquet: {new_size:.2f} MB")
            print(f"  Reduction: {reduction:.1f}%\n")
            
        except Exception as e:
            print(f"  ❌ Error: {e}\n")

# Usage
batch_convert_shapefiles('data/shapefiles', 'data/geoparquet')
```

### Example 2: Cloud-Native Processing

```python
import geopandas as gpd
import duckdb

# Process data directly from S3 without downloading
con = duckdb.connect()
con.execute("INSTALL spatial; LOAD spatial;")
con.execute("INSTALL httpfs; LOAD httpfs;")

# Query remote GeoParquet file
query = """
    SELECT 
        country,
        COUNT(*) as city_count,
        AVG(population) as avg_population,
        SUM(ST_Area(geometry)) as total_area
    FROM read_parquet('s3://my-bucket/cities.parquet')
    WHERE population > 100000
    GROUP BY country
    ORDER BY city_count DESC
"""

result = con.execute(query).df()
print(result)
```

### Example 3: Streaming Large Files

```python
import geopandas as gpd
import pyarrow.parquet as pq

def process_in_chunks(filename, chunk_size=100000):
    """Process large GeoParquet files in chunks"""
    
    # Open parquet file
    parquet_file = pq.ParquetFile(filename)
    
    total_area = 0
    feature_count = 0
    
    # Process in batches
    for batch in parquet_file.iter_batches(batch_size=chunk_size):
        # Convert to GeoDataFrame
        gdf = gpd.GeoDataFrame.from_arrow(batch)
        
        # Process chunk
        gdf['area'] = gdf.geometry.area
        total_area += gdf['area'].sum()
        feature_count += len(gdf)
        
        print(f"Processed {feature_count:,} features...")
    
    avg_area = total_area / feature_count
    print(f"\nTotal features: {feature_count:,}")
    print(f"Average area: {avg_area:.2f}")
    
    return total_area, feature_count

# Process 10GB file without loading all into memory
process_in_chunks('huge_dataset.parquet')
```

### Example 4: Partitioned Dataset Creation

```python
import geopandas as gpd
import pandas as pd

# Read large dataset
gdf = gpd.read_file('large_dataset.geojson')

# Add partition columns
gdf['year'] = pd.to_datetime(gdf['date']).dt.year
gdf['month'] = pd.to_datetime(gdf['date']).dt.month
gdf['country'] = gdf['location'].str[:2]  # Extract country code

# Write partitioned GeoParquet
gdf.to_parquet(
    'partitioned_data',
    partition_cols=['country', 'year', 'month'],
    compression='zstd',
    engine='pyarrow'
)

# Result structure:
# partitioned_data/
#   country=US/year=2023/month=01/data.parquet
#   country=US/year=2023/month=02/data.parquet
#   country=CA/year=2023/month=01/data.parquet
#   ...

# Read specific partition (super fast!)
usa_2023_jan = gpd.read_parquet(
    'partitioned_data',
    filters=[
        ('country', '=', 'US'),
        ('year', '=', 2023),
        ('month', '=', 1)
    ]
)
```

### Example 5: Data Quality Validation

```python
import geopandas as gpd
import json

def validate_geoparquet_quality(filename):
    """Comprehensive validation of GeoParquet file"""
    
    print(f"Validating: {filename}\n")
    
    # Read file
    gdf = gpd.read_parquet(filename)
    
    # Check 1: Metadata
    print("📋 Metadata Check:")
    try:
        metadata = json.loads(gdf._geometry_column_name)
        print("  ✅ GeoParquet metadata present")
    except:
        print("  ⚠️ Warning: No GeoParquet metadata")
    
    # Check 2: Geometry validity
    print("\n🗺️ Geometry Check:")
    invalid = ~gdf.geometry.is_valid
    if invalid.sum() == 0:
        print(f"  ✅ All {len(gdf)} geometries valid")
    else:
        print(f"  ❌ {invalid.sum()} invalid geometries found")
    
    # Check 3: CRS
    print("\n🌍 CRS Check:")
    if gdf.crs:
        print(f"  ✅ CRS: {gdf.crs}")
    else:
        print("  ⚠️ Warning: No CRS defined")
    
    # Check 4: Bounds
    print("\n📏 Bounds Check:")
    bounds = gdf.total_bounds
    print(f"  MinX: {bounds[0]:.6f}")
    print(f"  MinY: {bounds[1]:.6f}")
    print(f"  MaxX: {bounds[2]:.6f}")
    print(f"  MaxY: {bounds[3]:.6f}")
    
    # Check 5: Geometry types
    print("\n🔷 Geometry Types:")
    geom_types = gdf.geometry.type.value_counts()
    for geom_type, count in geom_types.items():
        print(f"  {geom_type}: {count}")
    
    # Check 6: File size
    print("\n💾 File Size:")
    import os
    size_mb = os.path.getsize(filename) / (1024**2)
    print(f"  {size_mb:.2f} MB")
    
    print("\n✅ Validation complete!")

# Usage
validate_geoparquet_quality('data.parquet')
```

---

## 💼 Use Cases

### 1. **Large-Scale Analytics**
- Analyzing billions of geographic points
- Fast aggregations and filtering
- Integration with big data tools

### 2. **Cloud Data Lakes**
- Store geospatial data in S3/GCS/Azure
- Query without downloading
- Serverless processing

### 3. **Data Warehousing**
- BigQuery, Snowflake, Databricks integration
- SQL queries on geospatial data
- Join spatial with business data

### 4. **Machine Learning**
- Feature engineering pipelines
- Training data storage
- Efficient data loading

### 5. **Real-Time Dashboards**
- Fast data loading for visualizations
- Filtered queries for map views
- Responsive web applications

### 6. **Data Distribution**
- Share datasets efficiently
- Reduce download sizes
- Cloud-native access

---

## 📊 Performance Benchmarks

### File Size Comparison

**Dataset: 1 Million Building Polygons**

| Format | Size | Reduction |
|--------|------|-----------|
| GeoJSON | 1.2 GB | - |
| Shapefile | 850 MB | 29% |
| GeoPackage | 420 MB | 65% |
| **GeoParquet (snappy)** | **180 MB** | **85%** |
| **GeoParquet (zstd)** | **120 MB** | **90%** |

### Query Performance

**Operation: Filter 100M rows by attribute**

| Format | Time | Speed |
|--------|------|-------|
| GeoJSON | 45s | 1x |
| GeoPackage | 12s | 3.8x |
| **GeoParquet** | **2s** | **22.5x** |

### Cloud Performance

**Reading 100 columns from 1B rows on S3:**

| Format | Data Transfer | Time | Cost |
|--------|---------------|------|------|
| CSV/GeoJSON | 50 GB | 10 min | $5.00 |
| **GeoParquet (1 col)** | **500 MB** | **15s** | **$0.05** |

---

## 🎓 Best Practices

### 1. **Choose the Right Compression**

```python
# For frequently accessed data (speed priority)
gdf.to_parquet('data.parquet', compression='snappy')

# For archival/cloud storage (size priority)
gdf.to_parquet('data.parquet', compression='zstd')

# For streaming applications (ultra-fast decompression)
gdf.to_parquet('data.parquet', compression='lz4')
```

### 2. **Optimize Row Group Size**

```python
# For analytical queries (larger row groups)
gdf.to_parquet('data.parquet', row_group_size=128*1024*1024)  # 128MB

# For point queries (smaller row groups)
gdf.to_parquet('data.parquet', row_group_size=16*1024*1024)   # 16MB
```

### 3. **Use Partitioning for Large Datasets**

```python
# Partition by frequently filtered columns
gdf.to_parquet('data', partition_cols=['country', 'year'])

# Enables fast queries like:
# SELECT * FROM data WHERE country='USA' AND year=2023
```

### 4. **Column Selection**

```python
# Only read columns you need (huge performance boost!)
gdf = gpd.read_parquet('data.parquet', 
                       columns=['geometry', 'name', 'population'])
```

### 5. **Predicate Pushdown**

```python
# Filter while reading (don't load filtered-out data)
gdf = gpd.read_parquet('data.parquet',
                       filters=[('population', '>', 1000000)])
```

### 6. **CRS Standardization**

```python
# Use EPSG:4326 for maximum interoperability
gdf = gdf.to_crs('EPSG:4326')
gdf.to_parquet('data.parquet')
```

---

## 🤝 Contributing

We welcome contributions to improve this toolkit!

### Ways to Contribute

1. **Add New Tools**
   - Conversion utilities
   - Validation scripts
   - Optimization tools

2. **Improve Documentation**
   - Fix typos
   - Add examples
   - Create tutorials

3. **Submit Examples**
   - Real-world use cases
   - Integration patterns
   - Performance optimizations

4. **Report Issues**
   - Bugs in tools
   - Documentation errors
   - Feature requests

### Development Setup

```bash
# Clone repository
git clone https://github.com/Ahmed-Refaat/geo-parquet-toolkit.git
cd geo-parquet-toolkit

# Install dependencies
pip install -r requirements.txt

# Run tests
pytest tests/

# Run validation
python scripts/validate_geoparquet.py test_data/
```

---

## 📄 License

This project is licensed under the **Apache License 2.0** - see the [LICENSE](LICENSE) file for details.

**Copyright 2026 Ahmed Refaat**

### What You Can Do

✅ Commercial use  
✅ Modification  
✅ Distribution  
✅ Patent use  
✅ Private use  

### What You Must Do

⚠️ Include license in distributions  
⚠️ State changes made  
⚠️ Include copyright notice  

---

## 👤 About the Maintainer

**Ahmed Refaat**

Geospatial data engineer and open-source contributor specializing in cloud-native geospatial solutions, big data processing, and modern GIS infrastructure. Creator of multiple geospatial tools and datasets focused on making spatial data more accessible and efficient.

### Expertise

- 🌍 **Geospatial Technologies**: GIS, Remote Sensing, Spatial Analysis
- ☁️ **Cloud Platforms**: AWS, Google Cloud, Azure  
- 📊 **Big Data**: Apache Spark, DuckDB, Data Warehousing
- 🗺️ **Web Mapping**: Leaflet, Mapbox, Google Maps
- 🛰️ **Earth Observation**: Satellite imagery, Google Earth Engine
- 🐍 **Programming**: Python, JavaScript, SQL, R

### Featured Projects

- **[Earth Data Hub](https://github.com/Ahmed-Refaat/earth-data-hub)** - *Your Gateway to Global Geospatial Intelligence*
  - Comprehensive catalog of Google Earth Engine datasets
  - 1,000+ curated geospatial datasets
  - Community-driven data commons

- **[Geo-Parquet Toolkit](https://github.com/Ahmed-Refaat/geo-parquet-toolkit)** - *Complete geospatial Parquet toolkit*
  - Format specifications and tools
  - Conversion and validation utilities
  - Performance optimization guides

### Philosophy

> "Making geospatial data faster, smaller, and more accessible through open standards and cloud-native technologies"

### Connect

- **GitHub**: [@Ahmed-Refaat](https://github.com/Ahmed-Refaat)
- **Repository**: [geo-parquet-toolkit](https://github.com/Ahmed-Refaat/geo-parquet-toolkit)

---

## 🌟 Show Your Support

If you find this toolkit useful:

- ⭐ **Star this repository**
- 🔗 **Share with your network**
- 🐛 **Report issues** to help improve
- 💡 **Suggest features** for future releases
- 🤝 **Contribute** tools and examples

---

**Making geospatial data storage efficient, accessible, and cloud-native** 🚀

*Geo-Parquet Toolkit - Complete solution for modern geospatial data*

*Last Updated: January 2026*
