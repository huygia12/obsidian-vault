---
created: 1970-01-01T08:00
updated: 2024-04-25T10:18
tags:
  - API
  - SpringBoot
---

## Introduction
[Documentation](https://springdoc.org)
- Specific only for Spring boot.
- Swagger 2 does not support Spring boot 3.

[Open API dependency](https://mvnrepository.com/artifact/org.springdoc/springdoc-openapi-ui)
- Already include Swagger UI: `http://localhost:8080/swagger-ui/index.html`

## Enable open API with spring security
```
"/v3/api-docs",
"/v3/api-docs/**",
"/swagger-ui/**",
"/swagger-ui.html"
```

## Annotation
- `@Operation` chỉ định endpoint sẽ thêm document.
	```
	responses = {  
        @ApiResponse(responseCode="200", description="Success",  
                content = { @Content }),  
        @ApiResponse(responseCode="404", description="User not found",  
                content = { @Content(mediaType = "application/json")}),  
        @ApiResponse(responseCode="422", description="Invalid user",  
                content = { @Content(mediaType = "application/json",}),  
	}
	```
- Thêm annotation `@ResponseStatus` vào các function trả về ResponseEntity để tự động tạo document cho các mã phàn hồi (example value).
	- Thêm thuộc tính HttpStatus để xác định mã trả về.

## OpenAPI Configuration
```
@OpenAPIDefinition(  
        info = @Info(  
                contact = @Contact(  
                        name = "Huy",  
                        email = "@gmail.com"  
                ),  
                description = "OpenAPI documentation for ...",  
                title = "OpenAPI document",  
                license = @License()  
        ),  
        servers = {  
                @Server(  
                        description = "Local ENV",  
                        url = "http://localhost:8080"  
                ),  
                @Server(  
                        description = "PROD ENV",  
                        url = ""  
                )  
        }  
)
@SecurityScheme(  
        name = "bearerAuth",  
        description = "JWT auth description",  
        scheme = "bearer",  
        type = SecuritySchemeType.HTTP,  
        bearerFormat = "JWT",  
        in = SecuritySchemeIn.HEADER,  
          
)
public class OpenAPIConfiguration {  
}
```