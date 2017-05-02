---
title: "IDebugDocumentTextExternalAuthor::GetPathName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextExternalAuthor.GetPathName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentTextExternalAuthor::GetPathName"
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextExternalAuthor::GetPathName
ドキュメントの完全パスとファイル名を返します。  
  
## 構文  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### パラメーター  
 `pbstrLongName`  
 \[入力\]完全パスとファイル名を含むを文字列です。  
  
 `pfIsOriginalFile`  
 \[入力\]ファイル名とパスがドキュメントを参照する示すブール値。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_FAIL`|ソース ファイルを作成または判断できません。|  
  
## 解説  
 このメソッドは、ドキュメントの完全パスとファイル名を返します。  
  
 `pfIsOriginalFile` が false の場合、`pbstrLongName` のパスとファイル名は、新しく作成された一時ファイルを示します。  
  
## 参照  
 [IDebugDocumentTextExternalAuthor インターフェイス](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)