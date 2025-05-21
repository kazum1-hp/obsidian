一些动态变化特效
###### 三角波+呼吸效果

`float timeValue = glfwGetTime();`
`float base = (sin(timeValue * 2.0f) / 2.0f + 0.5f);`
`float pulse = abs(sin(timeValue * 5.0f));`

`vertices[3] = base;`
`vertices[10] = base;`
`vertices[17] = base;`
`vertices[4] = pulse;`
`vertices[11] = pulse;`
`vertices[15] = 1.0f - base;`
`vertices[5] = 1.0f - base;`
`vertices[9] = 1.0f - pulse;`
`vertices[16] = 1.0f - pulse;`

###### 响应鼠标

`double xpos, ypos;`
`glfwGetCursorPos(window, &xpos, &ypos);`

`float normalizedX = (xpos / SCR_WIDTH) * 2.0f - 1.0f;`
`float normalizedY = 1.0f - (ypos / SCR_HEIGHT) * 2.0f;`

`vertices[3] = normalizedX;`
`vertices[4] = normalizedY;`
`vertices[5] = abs(sin(timeValue));`

`vertices[10] = normalizedX;`
`vertices[11] = normalizedY;`
`vertices[9] = abs(sin(timeValue));`

`vertices[17] = normalizedX;`
`vertices[15] = normalizedY;`
`vertices[16] = abs(sin(timeValue));`
