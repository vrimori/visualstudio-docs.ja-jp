---
title: "IDiaSession::findInjectedSource | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSession::findInjectedSource メソッド"
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSession::findInjectedSource
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

コンパイル処理の属性プロバイダーまたは他のコンポーネントによってシンボル ストアに発行されたソースの一覧を取得します。  
  
## 構文  
  
```cpp#  
HRESULT findInjectedSource (   
   LPCOLESTR                 srcFile,  
   IDiaEnumInjectedSources** ppResult  
);  
```  
  
#### パラメーター  
 srcFile  
 \[入力\] 検索するソース ファイルの名前。  
  
 ppResult  
 \[入力\] 挿入されたソースすべての一覧を含む [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) のオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)