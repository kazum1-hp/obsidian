LearnOpenGL的第一课，在这之前配置好glfw库和GLAD，关于[[GLAD]]。

**初始化glfw**

	glfwInit(); //initialize GLFW
	glfwWindowHint(GLFW_CONTEXT_VERSION_MAJOR, 3); 
	glfwWindowHint(GLFW_CONTEXT_VERSION_MINOR, 3); //run at version3.3
	glfwWindowHint(GLFW_OPENGL_PROFILE, GLFW_OPENGL_CORE_PROFILE); //core-profile

**创建窗口实例**

	GLFWwindow* window = glfwCreateWindow(800, 600, "LearnOpenGL", NULL, NULL);
	if (window == NULL) {
		std::cout << "Failed to create GLFW window." << std::endl;
		glfwTerminate();
		return -1;
	}
	
	glfwMakeContextCurrent(window);

**初始化glad**

	if (!gladLoadGLLoader((GLADloadproc)glfwGetProcAddress)) {
		std::cout << "Failed to initialize GLAD." << std::endl;
		return -1;
	}

**设置视口（告诉OpenGL需要渲染的尺寸）**

	glViewport(0, 0, 800, 600); //set viewport dimension
	前两个单位以像素为单位控制窗口左下角的位置，后两个为宽度和高度

**设置回调函数（在窗口大小变化时）**

	void framebuffer_size_callback(GLFWwindow * window, int width, int height);

**渲染循环**

	//render loop
	while (!glfwWindowShouldClose(window)) {
		glfwSwapBuffers(window);
		glfwPollEvents();
	}


> **双缓冲(Double Buffer)**

应用程序使用单缓冲绘图时可能会存在图像闪烁的问题。 这是因为生成的图像不是一下子被绘制出来的，而是按照从左到右，由上而下逐像素地绘制而成的。最终图像不是在瞬间显示给用户，而是通过一步一步生成的，这会导致渲染的结果很不真实。为了规避这些问题，我们应用双缓冲渲染窗口应用程序。**前**缓冲保存着最终输出的图像，它会在屏幕上显示；而所有的的渲染指令都会在**后**缓冲上绘制。当所有的渲染指令执行完毕后，我们**交换**(Swap)前缓冲和后缓冲，这样图像就立即呈显出来，之前提到的不真实感就消除了。

**释放资源**

	glfwTerminate(); //release resources

**渲染清屏**
	自定义一个颜色清空屏幕，并清除颜色缓冲

		glClearColor(0.2f, 0.3f, 0.3f, 1.0f); //custom color for screen clean
		glClear(GL_COLOR_BUFFER_BIT); //buffer clear
