---
title: "SccAddFilesFromSCC 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccAddFilesFromSCC"
helpviewer_keywords: 
  - "SccAddFilesFromSCC 関数"
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# SccAddFilesFromSCC 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、ソース管理からファイルの一覧を現在開いているプロジェクトに追加します。  
  
## 構文  
  
```cpp  
SCCRTN SccAddFilesFromSCC(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LPSTR   lpUser,  
   LPSTR   lpAuxProjPath,  
   LONG    cFiles,  
   LPCSTR* lpFilePaths,  
   LPCSTR  lpDestination,  
   LPCSTR  lpComment,  
   LPBOOL  pbResults  
);  
```  
  
#### パラメーター  
 pContext  
 \[in\]ソース管理プラグインのコンテキストのポインター。  
  
 hwnd の分離  
 \[in\]ソース管理プラグインは、それによって提供されるダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 lpUser  
 \[入力、出力\]\(最大 SCC\_USER\_SIZE、null 終端文字を含む\) のユーザー名。  
  
 lpAuxProjPath  
 \[入力、出力\]プロジェクトを識別する補助型の文字列 \(最大 `SCC_PRJPATH_`サイズは、null 終端文字を含めて\)。  
  
 cFiles  
 \[in\]指定されたファイル数 `lpFilePaths`します。  
  
 lpFilePaths  
 \[入力、出力\]現在のプロジェクトに追加するファイル名の配列。  
  
 lpDestination  
 \[in\]ファイルが書き込まれる先のパス。  
  
 lpComment  
 \[in\]各追加されるファイルに適用されるコメントです。  
  
 pbResults  
 \[入力、出力\]エラーまたは 0 以外の値 \(TRUE\) に成功した場合に設定するフラグの配列 \(0 または FALSE\) ファイルごとに \(配列のサイズは以上である必要があります `cFiles` 長い\)。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_E\_PROJNOTOPEN|プロジェクトが開かれていません。|  
|SCC\_E\_OPNOTPERFORMED|指定された 1 つのプロジェクトに接続ではありません。 `lpAuxProjPath.`|  
|SCC\_E\_NOTAUTHORIZED|ユーザーは、データベースを更新する権限がありません。|  
|SCC\_E\_NONSPECIFICERROR|不明なエラーがあります。|  
|SCC\_I\_RELOADFILE|ファイルまたはプロジェクトを再読み込みする必要があります。|  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)