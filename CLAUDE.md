 
# Oqtane Module Development Rules

## PROJECT AWARENESS
- Always read module requirements from INITIAL.md or PRPs
- Check examples/ folder for Oqtane patterns to follow
- Understand this is an Oqtane CMS module project

## OQTANE ARCHITECTURE
- Follow 4-project structure: Client, Server, Shared, Package
- Use proper Oqtane base classes (ModuleBase, ServiceBase, etc.)
- Implement security with proper authorization attributes
- Include localization (.resx files) for all user-facing text

## CODE STRUCTURE
- Client: Blazor components inherit from ModuleBase
- Server: API controllers inherit from ModuleControllerBase  
- Shared: Models and interfaces
- Package: NuGet packaging and deployment

## REQUIRED PATTERNS
- Database migrations using Oqtane's migration system
- Proper dependency injection registration
- IAuditable implementation for all entities
- Authorization checks in all controllers