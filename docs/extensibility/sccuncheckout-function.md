---
title: "SccUncheckout 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccUncheckout"
helpviewer_keywords: 
  - "SccUncheckout 関数"
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccUncheckout 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、選択したファイルまたはファイルの内容をチェック アウト前の状態に復元できるため、前のチェック アウト操作を元に戻します。 チェック アウト後、ファイルに加えられたすべての変更は失われます。  
  
## 構文  
  
```cpp#  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### パラメーター  
 pvContext  
 \[in\]ソース管理プラグイン コンテキスト構造体。  
  
 hwnd の分離  
 \[in\]ソース管理プラグインは、それによって提供されるダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 nFiles  
 \[in\]指定されたファイルの数、 `lpFileNames` 配列。  
  
 lpFileNames  
 \[in\]チェック アウトを解除する対象のファイルの完全修飾パス名の配列。  
  
 される  
 \[in\]\(不使用\) コマンドのフラグです。  
  
 pvOptions  
 \[in\]ソース管理プラグインに固有のオプションです。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|チェック アウトの取り消しに成功しました。|  
|SCC\_E\_FILENOTCONTROLLED|選択したファイルはソース コード管理下ではありません。|  
|SCC\_E\_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題が原因と思わのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC\_E\_NONSPECIFICERROR|不特定のエラーです。 元に戻すチェック アウトは成功しませんでした。|  
|SCC\_E\_NOTCHECKEDOUT|ユーザーには、ファイルをチェック アウトはありません。|  
|SCC\_E\_NOTAUTHORIZED|この操作を実行できません。|  
|SCC\_E\_PROJNOTOPEN|ソース管理からプロジェクトが開かれていません。|  
|SCC\_I\_OPERATIONCANCELED|操作が完了する前に取り消されました。|  
  
## 解説  
 この操作の後、 `SCC_STATUS_CHECKEDOUT` と `SCC_STATUS_MODIFIED` フラグはどちらもクリアされますチェック アウトの取り消しが実行されたファイルです。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)