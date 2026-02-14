# Visual Studio Project Updates for Ruby 3.2

## Changes Needed to msp_lib.vcxproj

Add this configuration block to the project file (after the Ruby 2.5 configuration):

```xml
<!-- Ruby 3.2 x64 Release Configuration -->
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release (3.2)|x64'" Label="Configuration">
  <ConfigurationType>DynamicLibrary</ConfigurationType>
  <UseDebugLibraries>false</UseDebugLibraries>
  <PlatformToolset>v142</PlatformToolset>
  <WholeProgramOptimization>true</WholeProgramOptimization>
  <CharacterSet>MultiByte</CharacterSet>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release (3.2)|x64'">
  <LinkIncremental>false</LinkIncremental>
  <OutDir>$(SolutionDir)$(Platform)\$(Configuration)\$(ProjectName)\</OutDir>
  <IntDir>$(Platform)\$(Configuration)\$(ProjectName)\</IntDir>
  <TargetName>msp_lib</TargetName>
  <TargetExt>.so</TargetExt>
</PropertyGroup>

<ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release (3.2)|x64'">
  <ClCompile>
    <WarningLevel>Level3</WarningLevel>
    <Optimization>MaxSpeed</Optimization>
    <FunctionLevelLinking>true</FunctionLevelLinking>
    <IntrinsicFunctions>true</IntrinsicFunctions>
    <PreprocessorDefinitions>WIN32;_WIN_64_VER;NDEBUG;_WINDOWS;_USRDLL;MSP_EXPORTS;MSP_USE_SDL;HAVE_RUBY_ENCODING_H;RUBY_VERSION32;%(PreprocessorDefinitions)</PreprocessorDefinitions>
    <AdditionalIncludeDirectories>$(SolutionDir)..\..\ThirdParty\Ruby\include\3.2\win32_x64;$(SolutionDir)..\..\ThirdParty\NewtonDynamics\dgNewton;$(SolutionDir)..\..\ThirdParty\NewtonDynamics\dMath;$(SolutionDir)..\..\ThirdParty\SDL2\include;$(SolutionDir)..\..\ThirdParty\SDL2_mixer\include;%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
    <RuntimeLibrary>MultiThreadedDLL</RuntimeLibrary>
    <SDLCheck>true</SDLCheck>
  </ClCompile>
  <Link>
    <SubSystem>Windows</SubSystem>
    <GenerateDebugInformation>true</GenerateDebugInformation>
    <EnableCOMDATFolding>true</EnableCOMDATFolding>
    <OptimizeReferences>true</OptimizeReferences>
    <AdditionalDependencies>x64-vcruntime140-ruby320.lib;SDL2.lib;SDL2_mixer.lib;%(AdditionalDependencies)</AdditionalDependencies>
    <AdditionalLibraryDirectories>$(SolutionDir)..\..\ThirdParty\Ruby\lib\win32;$(SolutionDir)..\..\ThirdParty\SDL2\lib\x64;$(SolutionDir)..\..\ThirdParty\SDL2_mixer\lib\x64;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>
    <ModuleDefinitionFile>RubyExtension.def</ModuleDefinitionFile>
  </Link>
</ItemDefinitionGroup>
```

## ruby_prep.h Updates

Add this to ruby_prep.h after line 82:

```cpp
// Visual Studio 2019/2022 (for Ruby 3.2)
#if _MSC_VER >= 1920

    #ifdef RUBY_VERSION32
        // Ruby 3.2 specific definitions
        #define HAVE_NEXTAFTER 1
        #define HAVE_ACOSH 1
        #define HAVE_CBRT 1
        #define HAVE_ERF 1
        #define HAVE_TGAMMA 1
        #define HAVE_ROUND 1
        
        // Ruby 3.x compatibility macros
        #ifndef RARRAY_CONST_PTR
            #define RARRAY_CONST_PTR(a) RARRAY_PTR(a)
        #endif
        
        // Ruby 3.2 doesn't need ANYARGS
        #ifndef RUBY_ANYARGS_H
            #define RUBY_ANYARGS_H 1
        #endif
    #endif
    
#endif // VS 2019/2022
```

## MSPhysics.sln Updates

Add this configuration to the solution file:

```
Release (3.2)|x64 = Release (3.2)|x64
```

And in the project configuration mappings:

```
{PROJECT-GUID}.Release (3.2)|x64.ActiveCfg = Release (3.2)|x64
{PROJECT-GUID}.Release (3.2)|x64.Build.0 = Release (3.2)|x64
```

## File Locations

These files need to be updated:
- `C++Extension/Projects/VS/msp_lib.vcxproj`
- `C++Extension/Projects/VS/MSPhysics.sln`
- `C++Extension/Source/main/ruby_prep.h`
