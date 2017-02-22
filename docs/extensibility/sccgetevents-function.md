---
title: "SccGetEvents 関数 | Microsoft Docs"
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
  - "SccGetEvents"
helpviewer_keywords: 
  - "SccGetEvents 関数"
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# SccGetEvents 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、キューに置かれた状態のイベントを取得します。  
  
## 構文  
  
```cpp#  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### パラメーター  
 pvContext  
 \[in\]ソース管理プラグイン コンテキスト構造体。  
  
 lpFileName  
 \[入力、出力\]ソース管理プラグインが返されたファイル名 \(最大 \_MAX\_PATH 文字\) を格納するバッファー。  
  
 lpStatus  
 \[入力、出力\]ステータス コードを返します \(を参照してください [ファイルの状態コード](../extensibility/file-status-code-enumerator.md) 指定できる値について\)。  
  
 pnEventsRemaining  
 \[入力、出力\]この呼び出しの後、キューに残してエントリの数を返します。 呼び出すことが、呼び出し元がこの数値が大きい場合、 [SccQueryInfo](../extensibility/sccqueryinfo-function.md) 情報を一度にすべてを取得します。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|成功したイベントを取得します。|  
|SCC\_E\_OPNOTSUPPORTED|この関数がサポートされていません。|  
|SCC\_E\_NONSPECIFICERROR|不特定のエラーです。|  
  
## 解説  
 この関数は加えられていないかどうか、ソース管理下にあるファイルのステータスの更新を表示するアイドル状態の処理中に呼び出されます。 ソース管理プラグインが知っているすべてのファイルのステータスを維持し、変更されるたびに状態がによって示されたプラグイン、状態と関連付けられているファイルは、キューに格納します。 ときに `SccGetEvents` が呼び出されると、一番上のキューの要素が取得され、返されます。 この関数は、以前にキャッシュされた唯一の情報を返す制約し、非常に短時間 \(つまり、なし、ディスクの読み取り、または状態にソース管理システムを要求すること\)。 必要があります。それ以外の場合、IDE のパフォーマンスが低下する開始できます。  
  
 ソース管理プラグインが指すバッファーに空の文字列を格納するレポートへのステータスの更新がない場合は、 `lpFileName`です。 それ以外の場合、プラグインを格納、ファイルの完全なパス名にステータス情報が変更された適切なステータス コードが返されます \(で詳細に説明値の 1 つ [ファイルの状態コード](../extensibility/file-status-code-enumerator.md)\)。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [ファイルの状態コード](../extensibility/file-status-code-enumerator.md)