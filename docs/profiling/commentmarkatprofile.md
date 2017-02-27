---
title: "CommentMarkAtProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommentMarkAtProfile"
  - "CommentMarkAtProfileA"
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# CommentMarkAtProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`CommentMarkAtProfile` メソッドは、タイムスタンプ値、数値マーク、コメント文字列を .vsp ファイルに挿入します。  タイムスタンプ値を使用して外部イベントと同期できます。  マークとコメントを挿入するためには、CommentMarkAtProfile 関数を含むスレッドのプロファイルがオンに設定されている必要があります。  
  
## 構文  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (  
                                   __int64 dnTimestamp,  
                                   long lMarker,  
                                   LPCTSTR szComment);  
```  
  
#### パラメーター  
 `dnTimestamp`  
  
 タイムスタンプ値を表す 64 ビット整数値。  
  
 `lMarker`  
  
 挿入する数値マーカー。  マーカーは 0 以上の値にする必要があります。  
  
 `szComment`  
  
 挿入するテキスト文字列へのポインター。  この文字列は、NULL 終端文字を含めて 256 文字未満にする必要があります。  
  
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
 Mark コマンドまたは API 関数 \(CommentMarkAtProfile、CommentMarkProfile、または MarkProfile\) でマークとコメントが挿入されたとき、マークのプロファイル関数を含むスレッドでは、プロファイル状態をオンにする必要があります。  プロファイル マークは、スコープ内でグローバルです。  たとえば、あるスレッドに挿入したプロファイルマークを、.vsp ファイル内の任意のスレッドで使用し、データ セグメントの開始または終了をマークできます。  
  
> [!IMPORTANT]
>  CommentMarkAtProfile メソッドは、インストルメンテーションでのみ使用してください。  
  
## 同等の .NET Framework 関数  
 Microsoft.VisualStudio.Profiler.dll  
  
## 関数の情報  
  
|||  
|-|-|  
|**Header**|VSPerf.h をインクルードします。|  
|**ライブラリ**|VSPerf.lib を使用します。|  
|**Unicode**|CommentMarkAtProfileW \(Unicode\) および CommentMarkAtProfileA \(ANSI\) として実装されます。|  
  
## 使用例  
 次のコードは、CommentMarkAtProfile 関数の汎用的な呼び出しの例です。  ANSI 版の関数の呼び出しかどうかを判断するために Win32 の文字列マクロおよび ANSI のコンパイラ設定が使用されていることを前提としています。  
  
```  
void ExerciseCommentMarkAtProfile(void)  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkAtProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    int64 timeStamp = 0x1111;  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkAtProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkAtProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkAtProfile(  
        timeStamp,  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkAtProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
    pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## 参照  
 [Visual Studio プロファイラー API リファレンス \(ネイティブ\)](../profiling/visual-studio-profiler-api-reference-native.md)