---
title: "SccQueryChanges 関数 | Microsoft Docs"
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
  - "SccQueryChanges"
helpviewer_keywords: 
  - "SccQueryChanges 関数"
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# SccQueryChanges 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数では、指定されたコールバック関数を使用して各ファイルの名前の変更に関する情報を提供するファイルのリストを列挙します。  
  
## 構文  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### パラメーター  
 pContext  
 \[in\]ソース管理プラグインのコンテキストのポインター。  
  
 nFiles  
 \[in\]内のファイル数 `lpFileNames` 配列。  
  
 lpFileNames  
 \[in\]に関する情報を取得するファイル名の配列。  
  
 pfnCallback  
 \[in\]リスト内の各ファイル名に呼び出されるコールバック関数 \(を参照してください [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) 詳細\)。  
  
 pvCallerData  
 \[in\]コールバック関数に渡される値は変更されません。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|クエリの処理が正常に完了しました。|  
|SCC\_E\_PROJNOTOPEN|ソース管理にプロジェクトが開かれていません。|  
|SCC\_E\_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題が原因と思わのアクセスに関する問題が発生しました。|  
|SCC\_E\_NONSPECIFICERROR|指定されていないか、一般的なエラーが発生しました。|  
  
## 解説  
 クエリ対象の変更は、名前空間には: 具体的には、名前変更、追加すると、およびファイルを削除します。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [エラー コード](../extensibility/error-codes.md)