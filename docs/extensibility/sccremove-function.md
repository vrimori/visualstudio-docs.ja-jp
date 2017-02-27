---
title: "SccRemove 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccRemove"
helpviewer_keywords: 
  - "SccRemove 関数"
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccRemove 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、ソース管理システムからファイルを削除します。  
  
## 構文  
  
```cpp#  
SCCRTN SccRemove(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
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
 \[in\]削除するファイルの完全修飾パス名の配列。  
  
 lpComment  
 \[in\]削除される各ファイルに適用されるコメントです。  
  
 される  
 \[in\]コマンドのフラグ \(未使用\) です。  
  
 pvOptions  
 \[in\]ソース管理プラグインに固有のオプションです。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|アンインストールが正常に完了しました。|  
|SCC\_E\_FILENOTCONTROLLED|選択したファイルはソース管理下ではありません。|  
|SCC\_E\_OPNOTSUPPORTED|ソース管理システムでは、この操作はサポートされません。|  
|SCC\_E\_ISCHECKEDOUT|ユーザーを終了してからチェック アウトされているために、ファイルを削除できません。|  
|SCC\_E\_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題が原因と思わのアクセスに関する問題が発生しました。|  
|SCC\_E\_NOTAUTHORIZED|この操作を実行できません。|  
|SCC\_E\_NONSPECIFICERROR|不特定のエラーです。ファイルは削除されませんでした。|  
|SCC\_I\_OPERATIONCANCELED|操作が完了する前に取り消されました。|  
  
## 解説  
 この関数は、ソース管理システムからファイルを削除しますが、ユーザーのローカル ハード ドライブからは削除されません。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)