---
title: "SccHistory 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccHistory"
helpviewer_keywords: 
  - "SccHistory 関数"
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# SccHistory 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、指定されたファイルの履歴を表示します。  
  
## 構文  
  
```cpp#  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### パラメーター  
 `pvContext`  
 \[in\]ソース管理プラグイン コンテキスト構造体。  
  
 `hWnd`  
 \[in\]ソース管理プラグインは、それによって提供されるダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 `nFiles`  
 \[in\]指定されたファイルの数、 `lpFileName` 配列。  
  
 `lpFileName`  
 \[in\]ファイルの完全修飾名の配列。  
  
 `fOptions`  
 \[in\]\(現在は未使用\) コマンドのフラグです。  
  
 `pvOptions`  
 \[in\]ソース管理プラグインに固有のオプションです。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|バージョン履歴が正常に取得しました。|  
|SCC\_I\_RELOADFILE|実際には、ソース管理システムは \(たとえば、取得することによって、古いバージョンのこと\)、履歴をフェッチ中にディスク上のファイルを変更ため、IDE は、このファイルを再読み込みする必要があります。|  
|SCC\_E\_FILENOTCONTROLLED|ファイルはソース管理されていません。|  
|SCC\_E\_OPNOTSUPPORTED|ソース管理システムでは、この操作はサポートされません。|  
|SCC\_E\_NOTAUTHORIZED|この操作を実行できません。|  
|SCC\_E\_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題が原因と思わのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC\_E\_PROJNOTOPEN|プロジェクトになっているを開きます。|  
|SCC\_E\_NONSPECIFICERROR|不特定のエラーです。 ファイル履歴を取得できませんでした。|  
  
## 解説  
 ソース管理プラグインが各ファイルの履歴を表示する、独自のダイアログ ボックスを表示を使用して `hWnd` 親ウィンドウとします。 または、省略可能なテキストがコールバックを出力する関数が提供される、 [SccOpenProject](../extensibility/sccopenproject-function.md) 使用できますが、サポートされている場合。  
  
 注: 特定の状況ではこの呼び出しの実行中に検査するファイルが変更可能性があります。 たとえば、 [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] history コマンドは、ファイルの古いバージョンを取得する機会をユーザーに与えます。 このような場合は、ソース管理プラグインを返します。 `SCC_I_RELOAD` ファイルを再読み込みする必要があることを IDE に警告します。  
  
> [!NOTE]
>  ソース管理プラグインが配列の場合、ファイルのこの関数をサポートしない場合は、最初のファイルのファイル履歴のみを表示できます。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)