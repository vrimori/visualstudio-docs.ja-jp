---
title: "SccGetEvents 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetEvents
helpviewer_keywords: SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e2e9a22d0340774087fab8dd7dc564f415d9d9aa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sccgetevents-function"></a>SccGetEvents 関数
この関数は、キューに置かれた状態のイベントを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 lpFileName  
 [入力、出力].ソース管理プラグインが返されたファイル名 (最大 _MAX_PATH 文字) を格納するバッファー。  
  
 lpStatus  
 [入力、出力].ステータス コードを返します (を参照してください[ファイル ステータス コード](../extensibility/file-status-code-enumerator.md)使用可能な値)。  
  
 pnEventsRemaining  
 [入力、出力].この呼び出しの後、キュー内の残りのエントリの数を返します。 呼び出すことが呼び出し元がこの数値が大きい場合は、 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)情報を一度にすべてを取得します。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|成功したイベントを取得します。|  
|SCC_E_OPNOTSUPPORTED|この関数はサポートされていません。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>コメント  
 この関数は加えられていないかどうか、ソース管理下にあるファイルのステータスの更新を表示するアイドル状態の処理中に呼び出されます。 ソース管理プラグインを知っている、すべてのファイルの状態を維持し、変更されるたびに状態がによって示されたプラグイン、状態と関連付けられているファイルは、キューに格納します。 ときに`SccGetEvents`が呼び出されると、上部、キューの要素が取得され、返されます。 この関数は以前にキャッシュされた情報のみを返すには制限し、非常に迅速なターンアラウンドが実現 (つまり、なし、ディスクの読み取り、または状態のソース管理システムを求める); 必要があります。それ以外の場合、IDE のパフォーマンスが低下することに開始されます。  
  
 レポートへのステータスの更新がない場合は、ソース管理プラグインは、空の文字列を指すバッファーに格納`lpFileName`です。 それ以外の場合、プラグインを格納、ファイルの完全なパス名のステータス情報が変更され、適切なステータス コードを返します (で詳細に説明値の 1 つ[ファイル ステータス コード](../extensibility/file-status-code-enumerator.md))。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [ファイルの状態コード](../extensibility/file-status-code-enumerator.md)