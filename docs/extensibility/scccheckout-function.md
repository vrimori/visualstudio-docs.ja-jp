---
title: "SccCheckout 関数 | Microsoft Docs"
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
  - "SccCheckout"
helpviewer_keywords: 
  - "SccCheckout 関数"
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# SccCheckout 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

完全修飾ファイル名のリストを指定するには、この関数はそれらローカル ドライブです。 コメントは、チェック アウトされているすべてのファイルに適用されます。 コメントの引数を指定できます、 `null` 文字列。  
  
## 構文  
  
```cpp#  
SCCRTN SccCheckout (  
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
 \[in\]選択したファイルをチェック アウトの数。  
  
 lpFileNames  
 \[in\]チェック アウトするファイルの完全修飾パス名の配列。  
  
 lpComment  
 \[in\]これらのチェック アウトされている選択したファイルに適用されるコメントです。  
  
 される  
 \[in\]コマンドのフラグ \(を参照してください [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)\)。  
  
 pvOptions  
 \[in\]ソース管理プラグインに固有のオプションです。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|チェック アウトは成功しました。|  
|SCC\_E\_FILENOTCONTROLLED|選択したファイルはソース コード管理下ではありません。|  
|SCC\_E\_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題が原因と思わのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC\_E\_NOTAUTHORIZED|この操作を実行できません。|  
|SCC\_E\_NONSPECIFICERROR|不特定のエラーです。 が、ファイルをチェック アウトしません。|  
|SCC\_E\_ALREADYCHECKEDOUT|ユーザーでは、チェック アウトされているファイルが既に存在します。|  
|SCC\_E\_FILEISLOCKED|新しいバージョンの作成を禁止するファイルがロックされています。|  
|SCC\_E\_FILEOUTEXCLUSIVE|別のユーザーには、このファイルの排他チェック アウトが行われます。|  
|SCC\_I\_OPERATIONCANCELED|操作が完了する前に取り消されました。|  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)