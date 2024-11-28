https://www.bilibili.com/video/BV1rT411W7QM

https://www.bilibili.com/video/BV1mm4y1X7Hc

## 项目搭建

![image-20240913183204567](./images/image-20240913183204567.png)

前端创建后，也导入成module

## 配置security，返回json



![image-20240913193035873](./images/image-20240913193035873.png)

```java
Configuration
@EnableWebSecurity
public class SecurityConfiguration {
    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
        return http.authorizeHttpRequests()
                .anyRequest().authenticated()
                .and()
                .formLogin()
                .loginProcessingUrl("/api/auth/login")
                .successHandler(this::onAuthenticationSuccess)
                .failureHandler(this::onAuthenticationFailure)
                .and()
                .logout()
                .logoutUrl("/api/auth/logout")
                .and()
                .csrf()
                .disable()
                .exceptionHandling()
                .authenticationEntryPoint(this::onAuthenticationFailure )
                .and()
                .build();
    }
    public void onAuthenticationSuccess(HttpServletRequest request, HttpServletResponse response, Authentication authentication) throws IOException, ServletException {
        response.setCharacterEncoding("UTF-8");
        response.getWriter().write(JSON.toJSONString(RestBean.success("登录成功")));
    }
    public void onAuthenticationFailure(HttpServletRequest request, HttpServletResponse response, AuthenticationException exception) throws IOException, ServletException {
        response.setCharacterEncoding("UTF-8");
        response.getWriter().write(JSON.toJSONString(RestBean.failure(401, exception.getMessage())));
    }
}
```

![image-20240913195222273](./images/image-20240913195222273.png)