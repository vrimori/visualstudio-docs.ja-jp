---
title: "SccDirDiff 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccDirDiff"
helpviewer_keywords: 
  - "SccDirDiff 関数"
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# SccDirDiff 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、クライアントのディスク上の現在のローカル ディレクトリと、対応するプロジェクトをソース管理の違いを表示します。  
  
## 構文  
  
```cpp#  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### パラメーター  
 pContext  
 \[in\]ソース管理プラグイン コンテキスト構造体。  
  
 hwnd の分離  
 \[in\]ソース管理プラグインは、それによって提供されるダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 lpDirName  
 \[in\]視覚的な違いを表示対象のローカル ディレクトリへの完全修飾パス。  
  
 dwFlags  
 \[in\]コマンドのフラグ \(「解説」を参照してください\] セクション\)。  
  
 pvOptions  
 \[in\]ソース管理プラグインに固有のオプションです。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|ディスク上のディレクトリは、ソース コード管理のプロジェクトと同じです。|  
|SCC\_I\_FILESDIFFER|ディスク上のディレクトリは、ソース コード管理で、プロジェクトと異なります。|  
|SCC\_I\_RELOADFILE|ファイルまたはプロジェクトを再読み込みする必要があります。|  
|SCC\_E\_FILENOTCONTROLLED|ディレクトリは、ソース コード管理下ではありません。|  
|SCC\_E\_NOTAUTHORIZED|この操作を実行できません。|  
|SCC\_E\_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題が原因と思わのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|不特定のエラーです。|  
|SCC\_E\_FILENOTEXIST|ローカルのディレクトリが見つかりませんでした。|  
  
## 解説  
 この関数は、ソース管理ユーザーに指定したディレクトリへの変更の一覧を表示するプラグインに指示する使用されます。 プラグインは、ディスク上のユーザーのディレクトリと、対応するプロジェクトをバージョン管理の違いを表示する、任意の形式で、独自のウィンドウを開きます。  
  
 場合にすべてのディレクトリのプラグインがサポート比較では、「クイック比較」オプションがサポートされていない場合でも、ファイル名ごとにディレクトリの比較をサポートしてする必要があります。  
  
|`dwFlags`|解釈|  
|---------------|--------|  
|SCC\_DIFF\_IGNORECASE|大文字と小文字は \(クイック diff またはビジュアルのいずれかの使用可能性があります\)。|  
|SCC\_DIFF\_IGNORESPACE|\(クイック diff または visual 使用可能性があります\) の空白は無視されます。|  
|SCC\_DIFF\_QD\_CONTENTS|ソース管理プラグインのサポートを何も行わずに、ディレクトリでは、1 バイトずつを比較します。|  
|SCC\_DIFF\_QD\_CHECKSUM|プラグインでサポートされている、何も行わずに、チェックサムを使用してディレクトリを比較するか、サポートされていない場合はフォールバックして SCC\_DIFF\_QD\_CONTENTS 場合。|  
|SCC\_DIFF\_QD\_TIME|プラグインでサポートされている、サイレント モードで、タイムスタンプを使用してディレクトリを比較するか、サポートされていない場合はフォールバック SCC\_DIFF\_QD\_CHECKSUM または SCC\_DIFF\_QD\_CONTENTS 場合。|  
  
> [!NOTE]
>  この関数と同じコマンドのフラグを使用して、 [SccDiff](../extensibility/sccdiff-function.md)です。 ただし、ソース管理プラグインは、ディレクトリの「クイック比較」操作をサポートしていませんこともできます。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)