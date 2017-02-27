---
title: "StartProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "StartProfile"
ms.assetid: 1761311d-c9d5-48f5-b1f8-b3605829940a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# StartProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`StartProfile` 関数は、指定されたプロファイル レベルのカウンターを 1 \(オン\) に設定します。  
  
## 構文  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI StartProfile(  
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
 StartProfile および StopProfile によって、プロファイル レベルにおける開始\/停止状態を制御します。  開始\/停止の既定値は 1 です。  初期値はレジストリで変更できます。  StartProfile を呼び出すたびに、停止\/開始が 1 に設定されます。StopProfile を呼び出すたびに、停止\/開始が 0 に設定されます。  
  
 停止\/開始が 0 よりも大きい場合、そのレベルの停止\/開始状態はオンになります。  停止\/開始が 0  以下の場合、停止\/開始状態はオフになります。  
  
 開始\/停止状態と保留\/再開状態の両方がオンの場合、そのレベルのプロファイル状態はオンです。  プロファイルの対象となるスレッドでは、グローバル レベル状態、プロセス レベル状態、スレッド レベル状態がオンである必要があります。  
  
## 同等の .NET Framework 関数  
 Microsoft.VisualStudio.Profiler.dll  
  
## 関数の情報  
 ヘッダー : VSPerf.h で宣言  
  
 インポート ライブラリ : VSPerf.lib  
  
## 使用例  
 次に StartProfile 関数を呼び出す例を示します。  
  
```  
void ExerciseStartProfile()  
{  
    // StartProfile and StopProfile control the  
    // Start/Stop state for the profiling level.   
    // The default initial value of Start/Stop is 1.   
    // The initial value can be changed in the registry.   
    // Each call to StartProfile sets Start/Stop to 1;   
    // each call to StopProfile sets it to 0.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold return value of   
    // the call to StartProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = StartProfile(  
        PROFILE_THREADLEVEL,  
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