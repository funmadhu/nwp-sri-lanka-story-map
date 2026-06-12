# QGIS Layer Styles

## Government Offices Symbology

### Pradeshiya Sabha (Blue Circle)
```xml
<symbol>
  <layer type="SimpleMarker" name="layer0">
    <prop key="angle" v="0"/>
    <prop key="color" v="33,100,255,255"/>
    <prop key="horizontal_anchor_point" v="1"/>
    <prop key="joinstyle" v="bevel"/>
    <prop key="name" v="circle"/>
    <prop key="offset" v="0,0"/>
    <prop key="offset_map_unit_scale" v="3x:0,0,0,0,0,0"/>
    <prop key="offset_unit" v="MM"/>
    <prop key="outline_color" v="0,0,0,255"/>
    <prop key="outline_style" v="solid"/>
    <prop key="outline_width" v="0.2"/>
    <prop key="outline_width_map_unit_scale" v="3x:0,0,0,0,0,0"/>
    <prop key="outline_width_unit" v="MM"/>
    <prop key="scale_method" v="diameter"/>
    <prop key="size" v="6"/>
    <prop key="size_map_unit_scale" v="3x:0,0,0,0,0,0"/>
    <prop key="size_unit" v="MM"/>
    <prop key="vertical_anchor_point" v="1"/>
  </layer>
</symbol>
```

### Municipal (Red Square)
```xml
<symbol>
  <layer type="SimpleMarker" name="layer0">
    <prop key="angle" v="0"/>
    <prop key="color" v="255,50,50,255"/>
    <prop key="horizontal_anchor_point" v="1"/>
    <prop key="joinstyle" v="bevel"/>
    <prop key="name" v="square"/>
    <prop key="offset" v="0,0"/>
    <prop key="offset_map_unit_scale" v="3x:0,0,0,0,0,0"/>
    <prop key="offset_unit" v="MM"/>
    <prop key="outline_color" v="0,0,0,255"/>
    <prop key="outline_style" v="solid"/>
    <prop key="outline_width" v="0.2"/>
    <prop key="outline_width_map_unit_scale" v="3x:0,0,0,0,0,0"/>
    <prop key="outline_width_unit" v="MM"/>
    <prop key="scale_method" v="diameter"/>
    <prop key="size" v="6"/>
    <prop key="size_map_unit_scale" v="3x:0,0,0,0,0,0"/>
    <prop key="size_unit" v="MM"/>
    <prop key="vertical_anchor_point" v="1"/>
  </layer>
</symbol>
```

### District Secretariat (Green Triangle)
```xml
<symbol>
  <layer type="SimpleMarker" name="layer0">
    <prop key="angle" v="0"/>
    <prop key="color" v="50,200,50,255"/>
    <prop key="horizontal_anchor_point" v="1"/>
    <prop key="joinstyle" v="bevel"/>
    <prop key="name" v="triangle"/>
    <prop key="offset" v="0,0"/>
    <prop key="offset_map_unit_scale" v="3x:0,0,0,0,0,0"/>
    <prop key="offset_unit" v="MM"/>
    <prop key="outline_color" v="0,0,0,255"/>
    <prop key="outline_style" v="solid"/>
    <prop key="outline_width" v="0.2"/>
    <prop key="outline_width_map_unit_scale" v="3x:0,0,0,0,0,0"/>
    <prop key="outline_width_unit" v="MM"/>
    <prop key="scale_method" v="diameter"/>
    <prop key="size" v="7"/>
    <prop key="size_map_unit_scale" v="3x:0,0,0,0,0,0"/>
    <prop key="size_unit" v="MM"/>
    <prop key="vertical_anchor_point" v="1"/>
  </layer>
</symbol>
```

## Administrative Boundaries Symbology

### District Boundaries (Subtle line)
```xml
<symbol>
  <layer type="SimpleLine" name="outline">
    <prop key="capstyle" v="square"/>
    <prop key="customdash" v="5;2"/>
    <prop key="customdash_map_unit_scale" v="3x:0,0,0,0,0,0"/>
    <prop key="customdash_unit" v="MM"/>
    <prop key="draw_inside_polygon" v="0"/>
    <prop key="joinstyle" v="bevel"/>
    <prop key="line_color" v="150,150,150,255"/>
    <prop key="line_style" v="solid"/>
    <prop key="line_width" v="0.5"/>
    <prop key="line_width_unit" v="MM"/>
    <prop key="offset" v="0"/>
    <prop key="offset_map_unit_scale" v="3x:0,0,0,0,0,0"/>
    <prop key="offset_unit" v="MM"/>
    <prop key="ring_filter" v="0"/>
    <prop key="use_custom_dash" v="0"/>
    <prop key="width_map_unit_scale" v="3x:0,0,0,0,0,0"/>
  </layer>
</symbol>
```

## Usage in QGIS

1. Right-click layer → Properties → Symbology
2. Select "Categorized" or "Single Symbol"
3. Copy XML above into style definition
4. Adjust colors/sizes as needed
