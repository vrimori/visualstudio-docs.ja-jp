---
title: "IDispError::GetHelpInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetHelpInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetHelpInfo"
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetHelpInfo
エラーを説明するトピックのファイルとヘルプ コンテキスト ID のパスを、可能であれば返します。  
  
## 構文  
  
```  
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### パラメーター  
 `pbstrFileName`  
 \[入力\]ヘルプ ファイルの絶対パスを含むを文字列です。  ヘルプ ファイルがない場合、またはエラーが発生した場合、戻り値は null です。  
  
 `pdwContext`  
 \[入力\]エラーのヘルプ コンテキスト ID。   \( `pbstrFileName` が null のヘルプ ファイルが存在しない場合\)、このパラメーターは意味を持ちません。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_FAIL`|プロバイダー固有のエラーが発生しました。|  
|`E_INVALIDARG`|`pbstrFileName` か `pdwContext` は null でした。|  
|`E_OUTOFMEMORY`|プロバイダーはヘルプを返すようにファイル パスをする十分なメモリを割り当てられませんでした。|  
  
## 解説  
 このメソッドは、可能であればエラーを説明するトピックのファイルとヘルプ コンテキスト ID のパスを返します。  
  
> [!NOTE]
>  このメソッドは実装されていません。  
  
## 参照  
 [IDispError インターフェイス](../../winscript/reference/idisperror-interface.md)