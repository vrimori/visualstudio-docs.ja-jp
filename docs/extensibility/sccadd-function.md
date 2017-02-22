---
title: "SccAdd 関数 | Microsoft Docs"
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
  - "SccAdd"
helpviewer_keywords: 
  - "SccAdd 関数"
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# SccAdd 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、新しいファイルをソース管理システムに追加されます。  
  
## 構文  
  
```cpp#  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### パラメーター  
 pvContext  
 \[in\]ソース管理プラグイン コンテキスト構造体。  
  
 hwnd の分離  
 \[in\]ソース管理プラグインは、それによって提供されるダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 nFiles  
 \[in\]指定されている現在のプロジェクトに追加する選択したファイル数、 `lpFileNames` 配列。  
  
 lpFileNames  
 \[in\]追加するファイルの完全修飾のローカル名の配列。  
  
 lpComment  
 \[in\]追加されているファイルのすべてに適用されるコメントです。  
  
 pfOptions  
 \[in\]ファイル単位で提供されているコマンドのフラグの配列。  
  
 pvOptions  
 \[in\]ソース管理プラグインに固有のオプションです。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|追加操作が正常に完了しました。|  
|SCC\_E\_FILEALREADYEXISTS|選択したファイルは、既にソース管理下にあるいます。|  
|SCC\_E\_TYPENOTSUPPORTED|ソース管理システムでは、\(たとえば、バイナリ\) ファイルの種類はサポートされていません。|  
|SCC\_E\_OPNOTSUPPORTED|ソース管理システムでは、この操作はサポートされません。|  
|SCC\_E\_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題が原因と思わのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC\_E\_NOTAUTHORIZED|この操作を実行できません。|  
|SCC\_E\_NONSPECIFICERROR|不特定のエラーです。追加は実行されません。|  
|SCC\_I\_OPERATIONCANCELED|操作が完了する前に取り消されました。|  
|SCC\_I\_RELOADFILE|ファイルまたはプロジェクトを再読み込みする必要があります。|  
|SCC\_E\_FILENOTEXIST|ローカル ファイルが見つかりませんでした。|  
  
## 解説  
 通常の `fOptions` 、配列では、ここが置き換えられます `pfOptions`, 、いずれかで `LONG` ファイルごとの仕様のオプションです。 これは、ファイルの種類はファイルごとに異なる場合がありますので。  
  
> [!NOTE]
>  両方を指定することはできません `SCC_FILETYPE_TEXT` と `SCC_FILETYPE_BINARY` が同じファイルのオプションはどちらも指定します。 どちらの設定は、設定と同じ `SCC_FILETYPE_AUTO`, 、ソースがプラグインの初回ファイルの種類を管理する場合。  
  
 使用されているフラグの一覧を次に示します、 `pfOptions` 配列。  
  
|オプション|値|説明|  
|-----------|-------|--------|  
|SCC\_FILETYPE\_AUTO|0x00|ソース管理プラグインでは、ファイルの種類を検出する必要があります。|  
|SCC\_FILETYPE\_TEXT|0x01|ASCII テキスト ファイルを示します。|  
|SCC\_FILETYPE\_BINARY|0x02|ASCII テキスト以外のファイルの種類を示します。|  
|SCC\_ADD\_STORELATEST|0x04|デルタ ファイルの最新のコピーだけを格納しません。|  
|SCC\_FILETYPE\_TEXT\_ANSI|0x08|ANSI テキストとしてファイルを処理します。|  
|SCC\_FILETYPE\_UTF8|0x10|UTF8 形式での Unicode テキストとしてファイルを処理します。|  
|SCC\_FILETYPE\_UTF16LE|0x20|UTF16 に Unicode テキストとしてリトル エンディアン形式のファイルを扱います。|  
|SCC\_FILETYPE\_UTF16BE|0x40|UTF16 ビッグ エンディアン Unicode 文字列としてファイル形式を扱います。|  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)