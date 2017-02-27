---
title: "SccRunScc 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccRunScc"
helpviewer_keywords: 
  - "SccRunScc 関数"
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccRunScc 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、ソース管理の管理ツールを呼び出します。  
  
## 構文  
  
```cpp#  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
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
 \[in\]選択したファイル名の配列。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|ソース管理の管理ツールが正常に呼び出されます。|  
|SCC\_I\_OPERATIONCANCELED|操作が取り消されました。|  
|SCC\_E\_INITIALIZEFAILED|ソース管理システムを初期化できませんでした。|  
|SCC\_E\_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題が原因と思わのアクセスに関する問題が発生しました。|  
|SCC\_E\_CONNECTIONFAILURE|ソース管理システムに接続できませんでした。|  
|SCC\_E\_FILENOTCONTROLLED|選択したファイルはソース管理下ではありません。|  
|SCC\_E\_NONSPECIFICERROR|不特定のエラーです。|  
  
## 解説  
 この関数には、外部の管理ツールを介してさまざまなソース管理システムの機能にアクセスする呼び出し元ができます。 ソース管理システムがユーザー インターフェイスを持たない場合、ソース管理プラグインは必要な管理機能を実行するためのインターフェイスを実装できます。  
  
 この関数の数と、現在選択されているファイルのファイル名の配列。 管理インターフェイス内のファイルを事前に選択するファイルの一覧を使用できる、管理ツールをサポートする場合はそれ以外の場合、一覧を無視できます。  
  
 この関数は通常、ユーザーが選択したときに呼び出さ、 **起動 \< ソース管理サーバー \>** から、 **ファイル** \]\-\> \[ **ソース管理** メニュー。 これは、 **起動** メニュー オプションを常に無効になっているか、レジストリ エントリを設定しても非表示です。 詳細については、「[方法: ソース管理プラグインのインストール](../extensibility/internals/how-to-install-a-source-control-plug-in.md)」を参照してください。 場合にのみ、この関数が呼び出されます [SccInitialize](../extensibility/sccinitialize-function.md) 返します、 `SCC_CAP_RUNSCC` 機能ビット \(を参照してください [機能フラグ](../extensibility/capability-flags.md) 詳細についてはこのデバイスとその他の機能のビットで\)。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [方法: ソース管理プラグインのインストール](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [機能フラグ](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)