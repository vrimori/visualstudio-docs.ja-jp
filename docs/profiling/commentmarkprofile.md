---
title: "CommentMarkProfile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommentMarkProfile"
  - "CommentMarkProfileA"
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CommentMarkProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`CommentMarkProfile` 関数は、.vsp ファイルに数値マーカーと文字列を挿入します。  マークとコメントを挿入するためには、`CommentMarkProfile` 関数を含むスレッドのプロファイルがオンに設定されている必要があります。  
  
## 構文  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(  
                                   long lMarker,   
                                   LPCTSTR szComment);  
```  
  
#### パラメーター  
 `lMarker`  
  
 挿入する数値マーカー。  マーカーは 0 以上の値にする必要があります。  
  
 `szComment`  
  
 挿入するテキスト文字列へのポインタ。  この文字列は、NULL 終端文字を含めて 256 文字未満にする必要があります。  
  
## プロパティ値\/戻り値  
 関数の成功または失敗は、**PROFILE\_COMMAND\_STATUS** 列挙型を使って表されます。  戻り値は次のいずれかになります。  
  
|列挙子|説明|  
|---------|--------|  
|MARK\_ERROR\_MARKER\_RESERVED|パラメーターは 0 以下です。  これらの値は予約済みです。  マークとコメントは記録されません。|  
|MARK\_ERROR\_MODE\_NEVER|関数が呼び出されたときに、プロファイル モードが NEVER に設定されました。  マークとコメントは記録されません。|  
|MARK\_ERROR\_MODE\_OFF|関数が呼び出されたときに、プロファイル モードが OFF に設定されました。  マークとコメントは記録されません。|  
|MARK\_ERROR\_NO\_SUPPORT|このコンテキストでマークがサポートされていません。  マークとコメントは記録されません。|  
|MARK\_ERROR\_OUTOFMEMORY|メモリ不足のため、このイベントを記録できません。  マークとコメントは記録されません。|  
|MARK\_TEXTTOOLONG|文字列の長さが最大値の 256 文字を超えています。  コメント文字列は切り詰められ、マークとコメントが記録されます。|  
|MARK\_OK|成功した場合は MARK\_OK が返されます。|  
  
## 解説  
 VSInstr Mark コマンドまたは関数 \(CommentMarkAtProfile、CommentMarkProfile、または MarkProfile\) でマークとコメントが挿入されたとき、マークのプロファイル関数を含むスレッドでは、プロファイル状態をオンにする必要があります。  
  
 プロファイル マークは、スコープ内でグローバルです。  たとえば、あるスレッドに挿入したプロファイルマークを、.vsp ファイル内の任意のスレッドで使用し、データ セグメントの開始または終了をマークできます。  
  
> [!IMPORTANT]
>  CommentMarkProfile メソッドは、インストルメンテーションでのみ使用できます。  
  
## 同等の .NET Framework 関数  
 Microsoft.VisualStudio.Profiler.dll  
  
## 関数の情報  
  
|||  
|-|-|  
|**Header**|VSPerf.h をインクルードします。|  
|**ライブラリ**|VSPerf.lib を使用します。|  
|**Unicode**|`CommentMarkProfileW` \(Unicode\) および `CommentMarkProfileA` \(ANSI\) として実装します。|  
  
## 使用例  
 次のコードは、CommentMarkProfile 関数の呼び出しの例です。  [!INCLUDE[vcpransi](../profiling/includes/vcpransi_md.md)] 関数の呼び出しかどうかを判断するために、Win32 の文字列マクロおよび Unicode に関するコンパイラ設定が使用されていることを前提としています。  
  
```  
void ExerciseCommentMarkProfile()  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkProfile(  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## 参照  
 [Visual Studio プロファイラー API リファレンス \(ネイティブ\)](../profiling/visual-studio-profiler-api-reference-native.md)