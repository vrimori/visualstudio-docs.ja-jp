---
title: "PROFILE_CURRENTID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PROFILE_CURRENTID"
ms.assetid: 55ccf665-a05e-48c3-adf7-7714c0a9aaef
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# PROFILE_CURRENTID
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

PROFILE\_CURRENTID は、NameProfile、StartProfile、StopProfile、SuspendProfile、ResumeProfile の各関数の呼び出しでスレッド ID またはプロセス ID の疑似トークンを返します。  指定されたスレッドやプロセスではなく、現在のスレッドまたはプロセスで関数を実行する場合に使用します。  
  
## 使用例  
 PROFILE\_CURRENTID は VSPerf.h 内で次のように定義されます。  
  
```  
static const unsigned int PROFILE_CURRENTID = (unsigned int)-1;  
```  
  
## 使用例  
 次に PROFILE\_CURRENTID の使用例を示します。  この例では、[StartProfile](../profiling/startprofile.md) 関数の呼び出しで、現在のスレッドを識別するためのパラメーターとして、PROFILE\_CURRENTID を使用しています。  
  
```  
void ExerciseProfileCurrentID()  
{  
    // Declare ProfileOperationResult enumeration   
    // to hold return value of a call to StartProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    profileResult = StartProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("StartProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## 参照  
 [Visual Studio プロファイラー API リファレンス \(ネイティブ\)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [NameProfile](../profiling/nameprofile.md)   
 [ResumeProfile](../profiling/resumeprofile.md)   
 [StartProfile](../profiling/startprofile.md)   
 [StopProfile](../profiling/stopprofile.md)   
 [SuspendProfile](../profiling/suspendprofile.md)