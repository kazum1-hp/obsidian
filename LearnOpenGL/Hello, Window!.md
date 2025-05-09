LearnOpenGL的第一课，在这之前配置好glfw库和GLAD，关于[[GLAD]]。

初始化glfw

	glfwInit(); //initialize GLFW
	glfwWindowHint(GLFW_CONTEXT_VERSION_MAJOR, 3); 
	glfwWindowHint(GLFW_CONTEXT_VERSION_MINOR, 3); //run at version3.3
	glfwWindowHint(GLFW_OPENGL_PROFILE, GLFW_OPENGL_CORE_PROFILE); //core-profile

创建窗口实例

	GLFWwindow* window = glfwCreateWindow(800, 600, "LearnOpenGL", NULL, NULL);
	if (window == NULL) {
		std::cout << "Failed to create GLFW window." << std::endl;
		glfwTerminate();
		return -1;
	}
	
	glfwMakeContextCurrent(window);

初始化glad

	if (!gladLoadGLLoader((GLADloadproc)glfwGetProcAddress)) {
		std::cout << "Failed to initialize GLAD." << std::endl;
		return -1;
	}

设置视口（告诉OpenGL需要渲染的尺寸）

	glViewport(0, 0, 800, 600); //set viewport dimension
	前两个单位以像素为单位控制窗口左下角的位置，后两个为宽度和高度

设置回调函数（在窗口大小变化时调用）

	void framebuffer_size_callback(GLFWwindow * window, int width, int height);
