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

