Any process that uses COM must both initialize and uninitialize the COM library.

To use basic COM services, all COM threads of execution in clients and out-of-process servers must call either the [**CoInitialize**](https://learn.microsoft.com/en-us/windows/desktop/api/Objbase/nf-objbase-coinitialize) or the [**CoInitializeEx**](https://learn.microsoft.com/en-us/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex) function before calling any other COM function except memory allocation calls. **CoInitializeEx** replaces the other function, adding a parameter that allows you to specify the threading model of the thread: either apartment-threaded or free-threaded. A call to **CoInitialize** simply sets the threading model to apartment-threaded.
____
Tags : #os #win32