# MCJNI
a simple header file with macro define help Android JNI developer write cleaner code

#### #define java(type, name, ...) jni(nspace, type, name, __VA_ARGS__)

	please include the 'MCJNI.h' file into each JNI .c file
	and add the above java() macro define into each JNI .c file
	change the <nspace> into 'Java_packagename_classname'
	example: 'Java_com_android_gles3jni_GLES3JNILib'

	use the java() macro like this:
	--------------------------------------------------------------
	java(void, resize, jint width, jint height)
	{
		onResizeScreen(width, height);
	}

	java(void, step, voida)
	{
		onUpdate(0,0,0);
		onDraw();
	}
	--------------------------------------------------------------
	the macro need at least one argument
	if the function have no argument use 'voida' as placeholder

	each JNI function have two hidden arguments
	1. JNIEnv* env
	2. jobject obj
	you can use 'env' & 'obj' access the JVM environment and Java object proxy
