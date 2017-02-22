---
title: "SccDirQueryInfo 関数 | Microsoft Docs"
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
  - "SccDirQueryInfo"
helpviewer_keywords: 
  - "SccDirQueryInfo 関数"
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# SccDirQueryInfo 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、その現在の状態の完全修飾ディレクトリの一覧を調べます。  
  
## 構文  
  
```cpp#  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### パラメーター  
 pContext  
 \[in\]ソース管理プラグイン コンテキスト構造体。  
  
 nDirs  
 \[in\]照会する選択されているディレクトリの数。  
  
 lpDirNames  
 \[in\]クエリを実行するディレクトリの完全修飾パスの配列。  
  
 lpStatus  
 \[入力、出力\]ソース管理の状態フラグを返すプラグインの配列構造体 \(を参照してください [ディレクトリの状態コード](../extensibility/directory-status-code-enumerator.md) 詳細\)。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|クエリは成功しました。|  
|SCC\_E\_OPNOTSUPPORTED|ソース コード管理システムでは、この操作はサポートされません。|  
|SCC\_E\_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題が原因と思わのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|不特定のエラーです。|  
  
## 解説  
 戻り値の配列からビットのビットマスクを埋める、 `SCC_DIRSTATUS` ファミリ \(を参照してください [ディレクトリの状態コード](../extensibility/directory-status-code-enumerator.md)\)、指定されたディレクトリごとに 1 つのエントリ。 状態配列は、呼び出し元によって割り当てられます。  
  
 IDE は、対応するプロジェクトがあるかどうかを照会することでディレクトリは、ソース管理下にあるかどうかをチェックするディレクトリの名前を変更する前に、この関数を使用します。 ディレクトリがソース管理下にない場合、IDE は、ユーザーに適切な警告を提供できます。  
  
> [!NOTE]
>  ソース管理プラグインのステータス値の 1 つ以上を実装しない場合、実装されていないビットが 0 に設定する必要があります。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [ディレクトリの状態コード](../extensibility/directory-status-code-enumerator.md)