---
title: "SccRename 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccRename"
helpviewer_keywords: 
  - "SccRename 関数"
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccRename 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、ソース管理システムでファイルを変更します。  
  
## 構文  
  
```cpp#  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### パラメーター  
 pvContext  
 \[in\]ソース管理プラグイン コンテキスト構造体。  
  
 hwnd の分離  
 \[in\]ソース管理プラグインは、それによって提供されるダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 lpFileName  
 \[in\]名前を変更するファイルの完全修飾ファイル名。  
  
 lpNewName  
 \[in\]完全修飾の新しい名前。 ディレクトリ パスが異なる場合、ファイルは移動 1 つのサブディレクトリから間です。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|名前の変更操作が正常に完了しました。|  
|SCC\_E\_PROJNOTOPEN|プロジェクトは、ソース管理下で開かれていません。|  
|SCC\_E\_FILENOTCONTROLLED|ファイルはソース管理されていません。|  
|SCC\_E\_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題が原因と思わのアクセスに関する問題が発生しました。|  
|SCC\_E\_NOTAUTHORIZED|ユーザーは、この操作を実行する権限がありません。|  
|SCC\_E\_COULDNOTCREATEPROJECT|名前の変更プロセスの一部として、プロジェクトを作成できませんでした。|  
|SCC\_E\_OPNOTPERFORMED|操作は実行されませんでした。|  
|SCC\_E\_NONSPECIFICERROR|指定されていないか、一般的なエラーが発生しました。|  
  
## 解説  
 この関数は、ファイル名を変更または 1 つの場所からに移動別、ソース管理システムで使用できます。 ソース管理プラグインでは、ディスク上のファイルにアクセスされません。 ローカル ファイルの名前を変更する IDE の役目です。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)