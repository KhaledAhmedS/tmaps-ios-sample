# tmaps-ios-sample

## Installation
### To integrate TMaps into your Xcode project, add it to your project:
1. Create folder named tmapswww
2. Download and Unzip map package inside tmapswww (Request map package from Tagipedia Team)
3. Read our sample for examples

## How it works
it works using dispatch actions between your APP and TMaps. So your APP dispatch actions to TMaps and TMaps dispatch actions to your APP.

## Usage
### TMaps actions dispatched to Your APP

#### <a name="READY">Ready</a>

dispatched when TMaps ready to receive dispatches from Your APP. So **you should not dispatch any action before TMaps get ready**.

```objc
@{
   @"type": @"READY"
};
```

___

#### <a name="MAP_LOADED">Map loaded</a>

dispatched when map loaded and visible to user.

```objc
@{
   @"type": @"MAP_LOADED"
};
```
___

#### Features tapped

dispatched when features in map tapped.

```objc
@{
   @"type": @"FEATURES_TAPPED",
   @"features": features
};
```

&nbsp;&nbsp;&nbsp;&nbsp;**features** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Required** *NSArray* with *NSDictionary*, each *NSDictionary* with *id*, *properties* keys

___

#### Associated feature tapped

dispatched when features in map tapped with the top feature visible to user.

```objc
@{
   @"type": @"ASSOCIATED_FEATURE_TAPPED",
   @"feature_id": feature_id,
   @"feature": feature
};
```

&nbsp;&nbsp;&nbsp;&nbsp;**feature_id** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Required** *NSString* with valid feature id

&nbsp;&nbsp;&nbsp;&nbsp;**feature** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Required** *NSDictionary* with *id*, *properties* keys

___

#### Category marked

dispatched when select category in map

```objc
@{
   @"type": @"CATEGORY_MARKED",
   @"category": category
};
```

&nbsp;&nbsp;&nbsp;&nbsp;**category** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Required** valid *NSString* category

___

#### Error

dispatched when error happened in TMaps

```objc
@{
   @"type": @"ERROR",
   @"error": error
};
```

&nbsp;&nbsp;&nbsp;&nbsp;**error** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Required** *NSDictionary* with *stack* key and *NSString* value

___

#### Feature marked

dispatched after MARK_FEATURE ended

```objc
@{
   @"type": @"FEATURE_MARKED",
   @"feature_id": feature_id
};
```

&nbsp;&nbsp;&nbsp;&nbsp;**feature_id** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Required** *NSString* with valid feature id

___

#### <a name="FEATURE_HIGHLIGHTED">Feature highlighted</a>

dispatched after HIGHLIGHT_FEATURE ended

```objc
@{
   @"type": @"FEATURE_HIGHLIGHTED",
   @"feature_id": feature_id
};
```

&nbsp;&nbsp;&nbsp;&nbsp;**feature_id** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Required** *NSString* with valid feature id

___

#### <a name="ZOOM_ENDED">Zoom ended</a>

dispatched after SET_ZOOM ended

```objc
@{
   @"type": @"ZOOM_ENDED"
};
```
___

#### <a name="CENTER_ENDED">Center ended</a>

dispatched after SET_CENTER ended

```objc
@{
   @"type": @"CENTER_ENDED"
};
```

___

#### <a name="EVENT_LOGGED">Event logged</a>

dispatched after any event happened in TMaps. Your app can send analytics after receive this action.

```objc
@{
   @"type": @"EVENT_LOGGED",
   @"event_category": @"Maps",
   @"event_action": @"Loaded",
   @"event_label": map_name,
   @"fields_object": @{
    @"map_id": map_id
   }
};
```

```objc
@{
   @"type": @"EVENT_LOGGED",
   @"event_category": @"Features",
   @"event_action": @"Tapped",
   @"event_label": feature_display_name,
   @"fields_object": @{
    @"map_id": map_id,
    @"feature_id": feature_id
   }
};
```

```objc
@{
   @"type": @"EVENT_LOGGED",
   @"event_category": @"Features",
   @"event_action": @"Highlighted",
   @"event_label": feature_display_name,
   @"fields_object": @{
    @"map_id": map_id,
    @"feature_id": feature_id
   }
};
```

```objc
@{
   @"type": @"EVENT_LOGGED",
   @"event_category": @"Features",
   @"event_action": @"Searched",
   @"event_label": feature_display_name,
   @"fields_object": @{
    @"map_id": map_id,
    @"feature_id": feature_id
   }
};
```

```objc
@{
   @"type": @"EVENT_LOGGED",
   @"event_category": @"Categories",
   @"event_action": @"Highlighted",
   @"event_label": category,
   @"fields_object": @{
    @"map_id": map_id
   }
};
```

```objc
@{
   @"type": @"EVENT_LOGGED",
   @"event_category": @"Categories",
   @"event_action": @"Searched",
   @"event_label": category,
   @"fields_object": @{
    @"map_id": map_id
   }
};
```

```objc
@{
   @"type": @"EVENT_LOGGED",
   @"event_category": @"Routes",
   @"event_action": @"Routed",
   @"event_label": source_display_name => target_display_name,
   @"fields_object": @{
    @"map_id": map_id,
    @"source_feature_id": source_feature_id,
    @"target_feature_id": target_feature_id
   }
};
```

```objc
@{
   @"type": @"EVENT_LOGGED",
   @"event_category": @"Buildings",
   @"event_action": @"Tapped",
   @"event_label": building_name,
   @"fields_object": @{
    @"map_id": map_id,
    @"building_id": building_id
   }
};
```

```objc
@{
   @"type": @"EVENT_LOGGED",
   @"event_category": @"Buildings",
   @"event_action": @"Opened",
   @"event_label": building_name,
   @"fields_object": @{
    @"map_id": map_id,
    @"building_id": building_id
   }
};
```

```objc
@{
   @"type": @"EVENT_LOGGED",
   @"event_category": @"Floors",
   @"event_action": @"Opened",
   @"event_label": floor_label,
   @"fields_object": @{
    @"map_id": map_id,
    @"layer_id": layer_id
   }
};
```

```objc
@{
   @"type": @"EVENT_LOGGED",
   @"event_category": @"RenderModes",
   @"event_action": @"Changed",
   @"event_label": render_mode,
   @"fields_object": @{
    @"map_id": map_id
   }
};
```



### <a name="your_app_to_tmaps">Your APP actions dispatched to TMaps</a>

#### <a name="set_tenant_data">Set tenant data</a>

dispatch it to set tenants of map. 

```objc
@{
   @"type": @"SET_TENANT_DATA",
   @"payload": tenants_json
};
```

&nbsp;&nbsp;&nbsp;&nbsp;**payload** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Required** *NSArray* with *NSDictionary*, each *NSDictionary* with *id*, *feature_id*, *name*, *booth_id*, *icon*, *CUSTOM_KEYS_YOU_NEED* keys

___

#### <a name="SET_DEFAULT_FEATURE_POPUP_TEMPLATE">Set default feature popup template</a>

dispatch it to change default feature popup template.

```objc
@{
   @"type": @"SET_DEFAULT_FEATURE_POPUP_TEMPLATE",
   @"template": template,
   @"template_custom_data": templateCustomData,
};
```

&nbsp;&nbsp;&nbsp;&nbsp;**template** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Required** valid *NSString* <a href="https://angular.io/guide/template-syntax">angular template</a> with <a href="#popup_scope">PopupScope</a> <br/>

&nbsp;&nbsp;&nbsp;&nbsp;<a name="template_custom_data">**template_custom_data**</a> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Optional** *NSDictionary* with *CUSTOM_KEYS_YOU_NEED* keys and *NSString*, *NSNumber*, *NSArray*, *NSDictionary* values <br/>
template custom data of keys that you want to use from <a href="#popup_scope_custom_data">customData</a> in <a href="#popup_scope">PopupScope</a>

___

#### Set theme

dispatch it to change theme of map.

```objc
@{
   @"primary": primary_color,
   @"accent": accent_color
};
```

&nbsp;&nbsp;&nbsp;&nbsp;**primary** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Optional** valid *NSString* color

&nbsp;&nbsp;&nbsp;&nbsp;**accent** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Optional** valid *NSString* color

___

#### Load map

dispatch it to load map.

```objc
@{
   @"type": @"LOAD_MAP",
   @"map_id": map_id,
   @"theme": @{
      @"primary": primary_color,
      @"accent": accent_color
   },
   @"center": @[lng, lat],
   @"zoom": zoom
};
```

&nbsp;&nbsp;&nbsp;&nbsp;**map_id** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Required** *NSString*

&nbsp;&nbsp;&nbsp;&nbsp;**theme** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Optional** *NSDictionary* with *primary*, *accent* keys and valid *NSString* color values
theme used for colors such as buttons and loading

&nbsp;&nbsp;&nbsp;&nbsp;**center** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Optional** *NSArray* of *NSNumbers*
Default map center in longitude and latitude

&nbsp;&nbsp;&nbsp;&nbsp;**zoom** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Optional** *NSNumber*
Default zoom level

___

#### Change render mode

dispatch it to change render mode.

```objc
@{
   @"type": @"CHANGE_RENDER_MODE",
   @"modeToRender": modeToRender
}
```

&nbsp;&nbsp;&nbsp;&nbsp;**modeToRender**
&nbsp;&nbsp;&nbsp;&nbsp;**Required** *NSString* with *2D*, *3D*

___


#### Set zoom

dispatch it to change zoom of map.

```objc
@{
   @"type": @"SET_ZOOM",
   @"zoom": zoom,
   @"zoom_type": zoom_type,
}
```

&nbsp;&nbsp;&nbsp;&nbsp;**zoom**
&nbsp;&nbsp;&nbsp;&nbsp;**Required** *NSNumber*

&nbsp;&nbsp;&nbsp;&nbsp;**zoom_type**
&nbsp;&nbsp;&nbsp;&nbsp;**Optional** *NSString* with *FLY_TO*

___

#### Set center

dispatch it to change center of map.

```objc
@{
   @"type": @"SET_CENTER",
   @"center": @[lng, lat],
}
```

&nbsp;&nbsp;&nbsp;&nbsp;**center**
&nbsp;&nbsp;&nbsp;&nbsp;**Required** *NSArray* of *NSNumbers*
Default map center in longitude and latitude

___

#### <a name="HIGHLIGHT_FEATURE">Highlight feature</a>

dispatch it to highlight feature.

```objc
@{
   @"type": @"HIGHLIGHT_FEATURE",
   @"feature_id": feature_id
}
```

&nbsp;&nbsp;&nbsp;&nbsp;**feature_id**
&nbsp;&nbsp;&nbsp;&nbsp;**Required** *NSString* with valid feature id

___

#### Mark feature

dispatch it to mark feature.

```objc
@{
   @"type": @"MARK_FEATURE",
   @"feature_id": feature_id
}
```

&nbsp;&nbsp;&nbsp;&nbsp;**feature_id**
&nbsp;&nbsp;&nbsp;&nbsp;**Required** *NSString* with valid feature id


## Types

### <a name="popup_scope">PopupScope</a>
#### poi

current feature

```js
poi
```

&nbsp;&nbsp;&nbsp;&nbsp;**poi**
&nbsp;&nbsp;&nbsp;&nbsp;**Required** *<a href="#poi">poi</a>*

___
#### enableRouting

*Boolean* to check if routing is enabled

```js
enableRouting
```
___
#### showRoutingDialog

method to show routing dialog.

```js
showRoutingDialog($event, data)
```

&nbsp;&nbsp;&nbsp;&nbsp;**$event**
&nbsp;&nbsp;&nbsp;&nbsp;**Required** *<a href="https://angular.io/guide/template-syntax#event-binding---event-">$event</a>*

&nbsp;&nbsp;&nbsp;&nbsp;**data**
&nbsp;&nbsp;&nbsp;&nbsp;**Optional** *Object* with *from*, *to* keys and *<a href="#poi">poi</a>* value

___
#### applyIfneeded

method to call <a href="https://docs.angularjs.org/api/ng/type/$rootScope.Scope#$apply">Angular $apply</a>

```js
applyIfneeded(callback)
```

&nbsp;&nbsp;&nbsp;&nbsp;**callback**
&nbsp;&nbsp;&nbsp;&nbsp;**Required** *Function*

___
#### <a name="popup_scope_custom_data">customData</a>

custom data object that have all keys of <a href="#template_custom_data">template_custom_data</a>

```js
customData[key]
```

&nbsp;&nbsp;&nbsp;&nbsp;**key**
&nbsp;&nbsp;&nbsp;&nbsp;**Required** with valid key from <a href="#template_custom_data">template_custom_data</a>
___
#### dispatch

method to dispatch action from your APP to TMaps.

```js
dispatch(action)
```

&nbsp;&nbsp;&nbsp;&nbsp;**action**
&nbsp;&nbsp;&nbsp;&nbsp;**Required** *Object* with valid <a href="#your_app_to_tmaps">action</a>
___
#### <a name="dispatchToContainer">dispatchToContainer</a>

method to dispatch action from TMaps to your APP.

```js
dispatchToContainer(action)
```

&nbsp;&nbsp;&nbsp;&nbsp;**action**
&nbsp;&nbsp;&nbsp;&nbsp;**Required** *Object* with *type*, *CUSTOM_KEYS_YOU_NEED* keys.<br />
*type* is *NSString* value.<br />
*CUSTOM_KEYS_YOU_NEED* is any of *NSString*, *NSNumber*, *NSArray*, *NSDictionary* values.<br />
___
#### closeInfo

method to close feature popup

```js
closeInfo()
```

### <a name="poi">poi</a>

#### id
id of feature

```js
poi.id
```
___
#### category
category of feature

```js
poi.category
```
___
#### tags

tags of feature

```js
poi.tags
```
___
#### getTenant

tenant of feature you set in <a href="#set_tenant_data">SET_TENANT_DATA</a>

```js
poi.getTenant()
```
___
#### <a name="getTenantName">getTenantName</a>

tenant name of feature you set in <a href="#set_tenant_data">SET_TENANT_DATA</a>

```js
poi.getTenantName()
```
___
#### <a name="getTenantIcon">getTenantIcon</a>

tenant icon of feature you set in <a href="#set_tenant_data">SET_TENANT_DATA</a>

```js
poi.getTenantIcon()
```
___
#### <a name="getTenantBoothId">getTenantBoothId</a>

tenant booth_id of feature you set in <a href="#set_tenant_data">SET_TENANT_DATA</a>

```js
poi.getTenantBoothId()
```
___
#### getDisplayName

<a href="#getTenantName">getTenantName</a> or feature name

```js
poi.getDisplayName()
```
___
#### hasName

check if tenant or feature have name. 

```js
poi.hasName()
```
___
#### isBuilding

check if feature is building.

```js
poi.isBuilding()
```
___
#### getIcon

<a href="#getTenantIcon">getTenantIcon</a> or feature icon

```js
poi.getIcon()
```
___
#### getBoothId

<a href="#getTenantBoothId">getTenantBoothId</a> or feature booth id

```js
poi.getBoothId()
```

## Advanced Scenrios (Look at sample for implementation of scenrios)

### Highlight initial feature

#### if you dispatch SET_ZOOM/SET_CENTER

you should dispatch <a href="#HIGHLIGHT_FEATURE">HIGHLIGHT_FEATURE</a> for initial feature after <a href="#ZOOM_ENDED">ZOOM_ENDED</a>/<a href="#CENTER_ENDED">CENTER_ENDED</a>

#### if you don't dispatch SET_ZOOM/SET_CENTER

you should dispatch <a href="#HIGHLIGHT_FEATURE">HIGHLIGHT_FEATURE</a> for initial feature after <a href="#MAP_LOADED">MAP_LOADED</a>

### Add custom buttons inside feature popup template

you should dispatch <a href="#SET_DEFAULT_FEATURE_POPUP_TEMPLATE">SET_DEFAULT_FEATURE_POPUP_TEMPLATE</a> for your customized template and add your custom buttons and use <a href="#dispatchToContainer">dispatchToContainer</a> when button clicked to handle the click action in your APP.







