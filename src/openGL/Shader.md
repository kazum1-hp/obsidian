`// ===== Render Loop =====`
`while (!glfwWindowShouldClose(window)) {`
	`processInput(window);`

	`// Clear screen`
	`glClearColor(0.2f, 0.3f, 0.3f, 1.0f); //custom color for screen clean`
	`glClear(GL_COLOR_BUFFER_BIT); //buffer clear`

	`// Draw` 
	`glUseProgram(shaderProgram);`

	`float timeValue = glfwGetTime();`
	`float greenValue = (sin(timeValue) / 2.0f) + 0.5f;`
	`int vertexColorLocation = glGetUniformLocation(shaderProgram, "ourColor");`
	`glUniform4f(vertexColorLocation, 0.0f, greenValue, 0.0f, 1.0f);`

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

	`/*double xpos, ypos;`
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
	`vertices[16] = abs(sin(timeValue));*/`


	`glBindBuffer(GL_ARRAY_BUFFER, VBO);`
	`glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC_DRAW);`


	`glBindVertexArray(VAO);`
	`glDrawArrays(GL_TRIANGLES, 0, 3);`

	`// Swap buffers and poll IO events`
	`glfwSwapBuffers(window);`
	`glfwPollEvents();`
`}`