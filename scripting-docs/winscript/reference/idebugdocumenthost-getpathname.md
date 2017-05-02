---
title: "IDebugDocumentHost::GetPathName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetPathName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetPathName"
ms.assetid: 8abe2a86-e467-4ac9-8ccb-8761141bfa0d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetPathName
ドキュメントのソース ファイルの完全パスとファイル名を返します。  
  
## 構文  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### パラメーター  
 `pbstrLongName`  
 \[入力\]長い名前を格納する文字列。  
  
 `pfIsOriginalFile`  
 \[入力\] `pbstrLongName` がドキュメントの元のファイルを参照する場合は false フラグ別の方法で。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_FAIL`|ソース ファイルを作成または判断できません。|  
  
## 解説  
 このメソッドは、文書のソース ファイルの完全パスとファイル名を返します。  
  
## 参照  
 [IDebugDocumentHost インターフェイス](../../winscript/reference/idebugdocumenthost-interface.md)