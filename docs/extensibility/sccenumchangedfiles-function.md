---
title: "SccEnumChangedFiles 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccEnumChangedFiles"
helpviewer_keywords: 
  - "SccEnumChangedFiles 関数"
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# SccEnumChangedFiles 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ローカル ファイルのリストを指定するには、この関数は、ファイルをソース コード管理データベースに対応するバージョンと異なるを決定します。  
  
## 構文  
  
```cpp  
SCCRTN SccEnumChangedFiles(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LONG    cFiles,  
   LPCSTR* lpFileNames,  
   LONG*   plIsFileDifferent  
);  
```  
  
#### パラメーター  
 pContext  
 \[in\]ソース管理プラグインのコンテキストのポインター。  
  
 hwnd の分離  
 \[in\]ソース管理プラグインは、それによって提供されるダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 cFiles  
 \[in\]指定されたファイル名の数、 `lpFileNames` 配列。 サイズを指定も `plIsFileDifferent` 配列。  
  
 lpFileNames  
 \[in\]チェックするローカル ファイル名の配列。  
  
 plIsFileDifferent  
 \[入力、出力\]各ファイルの相違点の状態を示す値の配列 \(配列が少なくとも必要 `cFiles` エントリ\)。 0 以外では、ファイルが異なることを意味します。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|操作が正常に完了しました。|  
|SCC\_UNSPECIFIEDERROR|一般エラーです。|  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)