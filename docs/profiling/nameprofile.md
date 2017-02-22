---
title: "NameProfile | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "NameProfile"
  - "NameProfileA"
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# NameProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`NameProfile` 関数は、指定したプロセスまたはスレッドに文字列を割り当てます。  
  
 NameProfile API は、インストルメンテーション プロファイリングでのみ使用できます。  NameProfile API は、サンプリング プロファイリングではサポートされません。  
  
## 構文  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(  
                                   LPCTSTR pszName,   
                                   PROFILE_CONTROL_LEVEL Level,  
                                   unsigned int dwId);  
```  
  
#### パラメーター  
 `pszName`  
  
 プロファイル要素の名前。  次の場合、名前は無効です \(NameProfileA は NAME\_ERROR\_INVALID\_NAME を返します\)。  
  
-   NameProfileA に渡されたポインターが NULL 値の場合  
  
-   pszName の文字列データの先頭が数値の場合  
  
-   pszName の文字列データに空白が含まれる場合  
  
-   pszName の文字列データにの次の文字が含まれる T: 、;。\`~\! @\#$%^\*& \(\) \= \[\] {}&#124;\\か。\/\<\>  
  
 `Level`  
  
 パフォーマンス データ収集を適用できるプロファイル レベルを指定します。  パフォーマンス データ収集を適用できるレベルには 3 つあり、**PROFILE\_CONTROL\_LEVEL** 値を使って指定できます。次のレベルのいずれかを指定できます。  
  
|列挙子|説明|  
|---------|--------|  
|PROFILE\_GLOBALLEVEL|グローバル レベル設定は、プロファイル実行のすべてのプロセスとスレッドに影響します。|  
|PROFILE\_PROCESSLEVEL|プロセス レベル設定は、指定されたプロセスに含まれるすべてのスレッドに影響します。|  
|PROFILE\_THREADLEVEL|スレッド プロファイル レベル設定は、指定されたスレッドに影響します。|  
  
 `dwId`  
  
 プロファイル レベル ID。  システムにより生成されたプロセス ID またはスレッド ID を使用します。  
  
## プロパティ値\/戻り値  
 関数の成功または失敗は、**PROFILE\_COMMAND\_STATUS** 列挙型を使って表されます。  戻り値は次のいずれかになります。  
  
|列挙子|説明|  
|---------|--------|  
|NAME\_ERROR\_ID\_NOEXIST|指定されたプロファイル要素が存在しません。|  
|NAME\_ERROR\_INVALID\_NAME|名前が無効です。|  
|NAME\_ERROR\_LEVEL\_NOEXIST|指定されたプロファイル レベルが存在しません。|  
|NAME\_ERROR\_NO\_SUPPORT|指定された操作がサポートされていません。|  
|NAME\_ERROR\_OUTOFMEMORY|メモリ不足のため、このイベントを記録できません。|  
|NAME\_ERROR\_REDEFINITION|このプロファイル要素には既に名前が割り当てられています。  この関数の名前は無視されます。|  
|NAME\_ERROR\_TEXTTRUNCATED|名前のテキストが null 文字を含めて 32 文字を超えていたため、切り詰められました。|  
|NAME\_OK|名前は正常に登録されました。|  
  
## 解説  
 各プロセスまたは各スレッドには、名前を 1 つのみ割り当てることができます。  プロファイル要素に名前を付けた後で、その要素の NameProfile を呼び出しても、無視されます。  
  
 異なるスレッドまたはプロセスに同じ名前が指定されている場合、その名前を持つそのレベルの全要素のデータがレポートに含まれます。  
  
 現在のプロセスまたはスレッド以外のプロセスまたはスレッドを指定した場合、それが初期化され実行が開始されていることを確認した後で名前を付ける必要があります。  初期化されず、実行が開始されていない場合、NameProfile メソッドは失敗します。  
  
> [!IMPORTANT]
>  スレッドまたはプロセスが初期化される前でも、CreateProcess\(\) API 関数および CreateThread\(\) API 関数は値を返します。  
  
## 同等の .NET Framework 関数  
 Microsoft.VisualStudio.Profiler.dll  
  
## 関数の情報  
  
|||  
|-|-|  
|**Header**|VSPerf.h をインクルードします。|  
|**ライブラリ**|VSPerf.lib を使用します。|  
|**Unicode**|`NameProfileW` \(Unicode\) および `NameProfileA` \(ANSI\) として実装します。|  
  
## 使用例  
 次のコードは、NameProfile 関数の呼び出しの例です。  ANSI 版の関数の呼び出しかどうかを判断するために Win32 の文字列マクロおよび ANSI のコンパイラ設定が使用されていることを前提としています。  
  
```  
void ExerciseNameProfile()  
{  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Create and initialize variables to pass to   
    // ExerciseNameProfile.  The value of this   
    // parameter is based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variable is assigned an arbitrary value.  
    TCHAR * profileName = TEXT("ExerciseNameProfile");  
  
    // Declare enumeration to hold result of call to   
    // ExerciseNameProfle.  
    PROFILE_COMMAND_STATUS nameResult;  
  
    nameResult =  NameProfile(  
        profileName,  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("NameProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, nameResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## 参照  
 [Visual Studio プロファイラー API リファレンス \(ネイティブ\)](../profiling/visual-studio-profiler-api-reference-native.md)