---
title: "ResumeProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ResumeProfile"
ms.assetid: 876f145b-ec07-4240-ade6-4f6e44baadce
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# ResumeProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`ResumeProfile` メソッドは、指定されたプロファイル レベルの保留\/再開カウンターをデクリメントします。  
  
## 構文  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI ResumeProfile(  
                       PROFILE_CONTROL_LEVEL Level,   
                       unsigned int dwId);  
```  
  
#### パラメーター  
 `Level`  
  
 パフォーマンス データ収集を適用できるプロファイル レベルを指定します。  パフォーマンス データ収集を適用できるレベルには 3 つあり、**PROFILE\_CONTROL\_LEVEL** 列挙子を使って指定できます。次のレベルのいずれかを指定できます。  
  
|列挙子|説明|  
|---------|--------|  
|PROFILE\_GLOBALLEVEL|グローバル レベル設定は、プロファイル実行のすべてのプロセスとスレッドに影響します。|  
|PROFILE\_PROCESSLEVEL|プロセス レベル設定は、指定されたプロセスに含まれるすべてのスレッドに影響します。|  
|PROFILE\_THREADLEVEL|スレッド プロファイル レベル設定は、指定されたスレッドに影響します。|  
  
 `dwId`  
  
 システムによって生成される、プロセスまたはスレッドの ID。  
  
## プロパティ値\/戻り値  
 関数の成功または失敗は、**PROFILE\_COMMAND\_STATUS** 列挙型を使って表されます。  戻り値は次のいずれかになります。  
  
|列挙子|説明|  
|---------|--------|  
|PROFILE\_ERROR\_ID\_NOEXIST|プロファイル要素 ID が存在しません。|  
|PROFILE\_ERROR\_LEVEL\_NOEXIST|指定されたプロファイル レベルが存在しません。|  
|PROFILE\_ERROR\_MODE\_NEVER|関数が呼び出されたときに、プロファイル モードが NEVER に設定されました。|  
|PROFILE\_ERROR\_NOT\_YET\_IMPLEMENTED|プロファイル関数呼び出し、プロファイル レベル、または呼び出しとレベルの組み合わせがまだ実装されていません。|  
|PROFILE\_OK|呼び出しに成功しました。|  
  
## 解説  
 保留\/再開カウンターの初期値は 0 です。  SuspendProfile を呼び出すたびに、保留\/再開数に 1 が加算されます。ResumeProfile を呼び出すたびに、1 が減算されます。  
  
 保留\/再開数が 0 よりも大きい場合、そのレベルの保留\/再開状態はオフになります。  保留\/再開数が 0 以下の場合、保留\/再開状態はオンになります。  
  
 開始\/停止状態と保留\/再開状態の両方がオンの場合、そのレベルのプロファイル状態はオンです。  プロファイルの対象となるスレッドでは、グローバル レベル状態、プロセス レベル状態、スレッド レベル状態がすべてオンである必要があります。  
  
## 同等の .NET Framework 関数  
 Microsoft.VisualStudio.Profiler.dll  
  
## 関数の情報  
 ヘッダー : VSPerf.h で宣言  
  
 インポート ライブラリ : VSPerf.lib  
  
## 使用例  
 次に ResumeProfile 関数の例を示します。  この例は、[PROFILE\_CURRENTID](../profiling/profile-currentid.md) で識別される同じスレッドまたはプロセスに対して、SuspendProfile メソッドが既に呼び出されていることを前提としています。  
  
```  
void ExerciseResumeProfile()  
{  
    // The initial value of the Suspend/Resume counter is 0.   
    // Each call to SuspendProfile adds 1 to the Suspend/Resume   
    // count; each call to ResumeProfile subtracts 1.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call to ResumeProfile  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = ResumeProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("ResumeProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## 参照  
 [Visual Studio プロファイラー API リファレンス \(ネイティブ\)](../profiling/visual-studio-profiler-api-reference-native.md)