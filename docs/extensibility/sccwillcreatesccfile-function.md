---
title: "SccWillCreateSccFile 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccWillCreateSccFile"
helpviewer_keywords: 
  - "SccWillCreateSccFile 関数"
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccWillCreateSccFile 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、ソース管理プラグインが、MSSCCPRJ の作成をサポートするかどうかを決定します。指定されたファイルごとの SCC ファイルです。  
  
## 構文  
  
```cpp#  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### パラメーター  
 pContext  
 \[in\]ソース管理プラグインのコンテキストのポインター。  
  
 nFiles  
 \[in\]含まれるファイル名の数、 `lpFileNames` 配列の長さだけでなく、 `pbSccFiles` 配列。  
  
 lpFileNames  
 \[in\]チェックする完全修飾ファイル名の配列 \(配列は呼び出し元が割り当てた必要があります\)。  
  
 pbSccFiles  
 \[入力、出力\]結果を格納する配列。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|成功。|  
|SCC\_E\_INVALIDFILEPATH|配列内のパスの 1 つは有効です。|  
|SCC\_E\_NONSPECIFICERROR|不特定のエラーです。|  
  
## 解説  
 この関数はかどうかは、ソース管理プラグインで使用できるように、MSSCCPRJ を確認するファイルの一覧が呼び出されます。\(詳細について、MSSCCPRJ 指定されたファイルの各 SCC ファイル。SCC ファイルを参照してください [MSSCCPRJ します。SCC ファイル](../extensibility/mssccprj-scc-file.md)\)。 ソース管理プラグインでは、MSSCCPRJ を作成する機能があるかどうかを宣言できます。宣言することでファイルを SCC `SCC_CAP_SCCFILE` の初期化中にします。 プラグインの戻り値を `TRUE` または `FALSE` の 1 ファイルあたり、 `pbSccFiles` MSSCCPRJ がある特定のファイルのうちの配列。SCC のサポート。 プラグインの成功コードが関数から返された場合は、戻り値の配列内の値が無視されます。 失敗した場合、配列は無視されます。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [MSSCCPRJ します。SCC ファイル](../extensibility/mssccprj-scc-file.md)