---
title: "IDiaDataSource::get_lastError | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaDataSource::get_lastError メソッド"
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::get_lastError
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

最後の読み込みエラーのファイル名を取得します。  
  
## 構文  
  
```cpp#  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### パラメーター  
 pRetVal  
 \[出力\] 最後の読み込みエラーと関連付けられた .pdb ファイル名を含む文字列を返します。  
  
## 戻り値  
 読み取り操作による最終エラー コードを返します。  `pRetVal` のパラメーターが `NULL` 場合 `E_INVALIDARG` を返します。  
  
## 使用例  
  
```cpp#  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## 参照  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)