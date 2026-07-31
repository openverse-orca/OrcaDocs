# What is the Asset Library and how to use it?

## Question
What is the Asset Library in OrcaLab? What does it contain? How can I effectively use the Asset Library for simulation project development?

## Answer

The **Asset Library** is one of OrcaLab's core components, providing a rich collection of digital assets such as 3D models, scenes, and robots. It is an essential resource platform for building simulation environments.

## 🏪 Asset Library Overview

### Definition & Purpose
The Asset Library is a **centralized digital asset management platform** that provides users with:
- 3D models and scene assets
- Robot models and configurations
- Physics simulation components
- AI training environment materials


### Access Methods
```bash
# Method 1: From the OrcaLab client
Click the [Open Asset Library] button

# Method 2: Direct URL access
https://simassets.orca3d.cn/
```

## 📁 Asset Library Category Structure

### 🏭 6 Major Categories

#### 1. **Industrial Assets**
```
Content: Machinery, production lines, industrial robots
Application: Manufacturing simulation, industrial automation training
Examples: Robotic arms, conveyor belts, assembly lines
```

#### 2. **Living Assets**
```
Content: Furniture, appliances, household items
Application: Service robot training, living scene simulation
Examples: Tables and chairs, refrigerators, tableware
```

#### 3. **Service Assets**
```
Content: Service venues, facilities and equipment
Application: Service industry simulation, scene modeling
Examples: Restaurants, hospitals, stores
```

#### 4. **Sensor Assets**
```
Content: Various sensor models
Application: Perception system simulation, data collection
Examples: Cameras, LiDAR, IMU
```

#### 5. **Robot Assets**
```
Content: Various robot models and configurations
Application: Robot control, behavior training
Examples: Quadruped robots, robotic arms, mobile chassis
```

#### 6. **Other Assets**
```
Content: Scene props, special-purpose assets
Application: Auxiliary modeling, specific requirements
Examples: Terrain, plants, decorations
```



## 🔍 Asset Search Features

### Search Methods

#### 🖼️ Image Search
```
Function: Search for similar assets by uploading a reference image
Best for: Quickly finding assets when you have a specific object image
How to: Upload image → AI recognition → Match results
```

#### 📝 Text Description Search
```
Function: Search via keyword text descriptions
Best for: When you know the general requirement but have no specific image
How to: Enter description → Keyword matching → Display results
```


### Search Tips
```
Keyword Strategies:
├── Use object names (e.g., "table", "robotic arm")
├── Use function descriptions (e.g., "grasping", "moving")
├── Use scene requirements (e.g., "kitchen", "factory")
└── Use brand/model names (e.g., "UR5", "Panda")

Combined Search:
├── "industrial robotic arm grasping"
├── "mobile robot navigation laser"
└── "quadruped walking dynamic"
```

## 📦 Asset Package Management

### Asset Package Concept
- An **asset package** is the basic management unit of the Asset Library
- One asset package contains 1 or more related assets
- Subscription and download are performed at the package level

### Asset Package Information
```
Basic Information:
├── Author information
├── Project name
├── Asset count
├── Total file size
├── Version information
└── Update time

Detailed Information:
├── Asset description
├── Usage instructions
├── Version changelog
├── Dependencies
└── Compatibility information
```



## 🔄 Asset Subscription Process

### Subscription Steps
```
1. Browse the Asset Library → Find the target asset package
2. View details → Confirm asset content and requirements
3. Click Subscribe → Add to personal asset library
4. Restart OrcaLab → Automatic download and sync
5. Assets available → Start using assets
```

### Subscription Management
```bash
After subscribing, asset packages will:
├── Appear in Personal Center
├── Be automatically downloaded locally
├── Be available in the OrcaLab client
└── Support version updates

Unsubscribing:
├── Removed from Personal Center
├── Local files retained
├── No longer available in client
└── Can re-subscribe
```



## 🤖 AI Generation Tools

### Tool Types

#### 🎨 Text-to-3D
```
Function: Generate 3D models from text descriptions
Input: Text description (e.g., "a red round table")
Output: USDZ format 3D asset
Quota: 5 times per day
```

#### 🖼️ Image-to-3D
```
Function: Generate 3D models from reference images
Input: 2D image file
Output: USDZ format 3D asset
Quota: 5 times per day
```


### Generation Parameter Descriptions
```
Parameter Configuration (recommended to keep defaults):
├── Separate Mesh: Split model components
├── Auto-generate LOD: Multi-level detail
├── Smooth Mesh: Surface smoothing
├── Smooth Strength: Processing intensity control
└── Use Hub CLI: Processing tool selection
```

### AI Generation Best Practices
```
Text Description Tips:
├── Be specific ("red wooden round table" is better than "table")
├── Include materials ("metal", "plastic", "wooden")
├── Specify size ("small", "medium", "large")
└── Add details ("with drawers", "four legs")

Image Selection Tips:
├── High clarity, good lighting
├── Target object centered and complete
├── Clean background, minimal distractions
└── Angle that showcases the object's main features
```

## 📱 Asset Library Usage Workflow

### 🎯 Project Planning Phase
```
1. Define simulation requirements
   ├── Scene type (indoor/outdoor/industrial)
   ├── Robot type (mobile/robotic arm/quadruped)
   ├── Task goals (grasping/navigation/detection)
   └── Accuracy requirements (teaching/research/product)

2. Search for relevant assets
   ├── Browse by category
   ├── Keyword search
   ├── Reference image search
   └── Note target asset packages
```

### 🔧 Asset Preparation Phase
```
3. Subscribe to necessary assets
   ├── Core scene assets
   ├── Main robot models
   ├── Required sensors
   └── Auxiliary prop assets

4. Asset download and sync
   ├── Restart OrcaLab to trigger download
   ├── Wait for sync to complete
   ├── Check asset integrity
   └── Verify asset availability
```

### 🚀 Project Development Phase
```
5. Build simulation scene
   ├── Select base scene
   ├── Drag and drop to add assets
   ├── Adjust position and pose
   └── Configure physical properties

6. Test and optimize
   ├── Run basic simulation
   ├── Check asset behavior
   ├── Optimize performance
   └── Save scene layout
```

## 💡 Advanced Usage Tips

### Asset Customization
```
Personal Asset Management:
├── AI-generate custom assets
├── Upload custom assets to personal library
├── Version management and updates
└── Share assets with others

Asset Optimization:
├── Choose LOD levels based on performance needs
├── Properly match materials and textures
├── Control scene complexity
└── Balance visual effects and performance
```

### Collaboration Workflows
```
Team Collaboration:
├── Uniformly subscribe to the same asset packages
├── Share custom assets
├── Standardize naming conventions
└── Version sync management

Project Management:
├── Record used asset lists
├── Back up important scene configurations
├── Document asset usage
└── Track asset version changes
```

## ⚠️ Usage Notes

### Copyright & Usage Restrictions
- Asset Library assets are for non-commercial use only
- No secondary distribution or commercial use
- AI-generated assets are also subject to non-commercial terms
- Respect original author copyright notices

### Performance Considerations
- Large asset packages consume significant storage space
- Complex assets affect simulation performance
- Choose assets wisely based on hardware configuration
- Periodically clean up unneeded asset packages

The Asset Library is an important component of the OrcaLab ecosystem. Properly utilizing Asset Library resources can greatly improve the development efficiency and quality of simulation projects.

## Related Links
- [Asset Library Basic Operation Guide](user-guide/asset-library-basic-operation-guide.md)
- [User Registration & Management](environment-setup/user-registration-and-management.md)
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)