---
title: "列挙子をメッセージ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6a24db9c50bd298f068c23af0b6bad5755ec252d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="message-enumerator"></a>メッセージの列挙子
次のフラグの使用、`TEXTOUTPROC`関数を呼び出すときに IDE が提供するコールバック関数、 [SccOpenProject](../extensibility/sccopenproject-function.md) (を参照してください[LPTEXTOUTPROC](../extensibility/lptextoutproc.md)詳細については、コールバックで関数の場合)。  
  
 プロセスをキャンセルする IDE が要求された場合では [キャンセル] メッセージのいずれかを取得する可能性があります。 この場合、ソースがプラグインで使用を制御`SCC_MSG_STARTCANCEL`に表示するための IDE を確認してください、**キャンセル**ボタンをクリックします。 その後、通常のメッセージの任意のセットを送信できます。 これらを返しますのいずれかの`SCC_MSG_RTN_CANCEL`、プラグインは、操作を終了し、返します、。 プラグインもポーリング`SCC_MSG_DOCANCEL`かどうか、ユーザーが操作の取り消しを確認するには、定期的にします。 すべての操作が完了したら、またはユーザーがキャンセルされた場合、プラグインは送信時に`SCC_MSG_STOPCANCEL`です。 `SCC_MSG_INFO`SCC_MSG_WARNING、SCC_MSG_ERROR 型は、メッセージの一覧に表示される取得されるメッセージに使用されます。 `SCC_MSG_STATUS`特殊な型を示すテキストがステータス バーまたは一時的な表示領域で現れる必要があります。 存在しません永続的に、一覧にします。  
  
## <a name="syntax"></a>構文  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## <a name="members"></a>メンバー  
 SCC_MSG_RTN_CANCEL  
 [キャンセル] を示すためにコールバックから戻る  
  
 SCC_MSG_RTN_OK  
 続行するコールバックから戻る  
  
 SCC_MSG_INFO  
 情報メッセージです。  
  
 SCC_MSG_WARNING  
 メッセージは警告です。  
  
 SCC_MSG_ERROR  
 メッセージは、エラーです。  
  
 SCC_MSG_STATUS  
 メッセージは、ステータス バーのものです。  
  
 SCC_MSG_DOCANCEL  
 テキストはありません。IDE を返します`SCC_MSG_RTN_OK`または`SCC_MSG_RTN_CANCEL`です。  
  
 SCC_MSG_STARTCANCEL  
 [キャンセル] ループを開始します。  
  
 SCC_MSG_STOPCANCEL  
 [キャンセル] ループを停止します。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)