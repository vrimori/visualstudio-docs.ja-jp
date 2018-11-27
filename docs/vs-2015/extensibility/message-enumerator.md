---
title: 列挙子のメッセージ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 63e878a408f242d50f12fda311257da6fe50fd1f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766526"
---
# <a name="message-enumerator"></a>メッセージの列挙子
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用は、次のフラグ、`TEXTOUTPROC`関数コールバック関数を呼び出すときに、IDE を提供しますが、 [SccOpenProject](../extensibility/sccopenproject-function.md) (を参照してください[LPTEXTOUTPROC](../extensibility/lptextoutproc.md)詳細については、コールバック関数の場合)。  
  
 IDE がプロセスをキャンセルしようとして、キャンセル メッセージのいずれかを受け取ること可能性があります。 ソース管理プラグインで使用でこの例では、`SCC_MSG_STARTCANCEL`を表示するための IDE を要求する、**キャンセル**ボタンをクリックします。 その後、通常のメッセージのセットを送信できます。 これらを返しますの`SCC_MSG_RTN_CANCEL`、プラグイン、操作を終了し、返します、。 プラグインもポーリング`SCC_MSG_DOCANCEL`かどうか、ユーザーが操作の取り消しを判断するには、定期的にします。 すべての操作が完了したら、またはユーザーがキャンセルされた場合、プラグインが送信時に`SCC_MSG_STOPCANCEL`します。 `SCC_MSG_INFO`SCC_MSG_WARNING、SCC_MSG_ERROR 型では、メッセージの一覧に表示されるメッセージが使用されます。 `SCC_MSG_STATUS` テキストがステータス バーまたは一時的な表示領域で表示していることを示す特殊な型です。 維持されない永続的に、一覧にします。  
  
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
 [キャンセル] を示すためにコールバックから返されます。  
  
 SCC_MSG_RTN_OK  
 続行するコールバックから返されます。  
  
 SCC_MSG_INFO  
 情報メッセージです。  
  
 SCC_MSG_WARNING  
 メッセージは警告です。  
  
 SCC_MSG_ERROR  
 メッセージは、エラーです。  
  
 SCC_MSG_STATUS  
 メッセージは、ステータス バーのものでは。  
  
 SCC_MSG_DOCANCEL  
 テキストはありません。IDE を返します`SCC_MSG_RTN_OK`または`SCC_MSG_RTN_CANCEL`します。  
  
 SCC_MSG_STARTCANCEL  
 [キャンセル] ループを開始します。  
  
 SCC_MSG_STOPCANCEL  
 [キャンセル] ループを停止します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)

