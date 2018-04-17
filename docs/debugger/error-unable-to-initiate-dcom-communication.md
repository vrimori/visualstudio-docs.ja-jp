---
title: 'エラー: DCOM 通信を開始できません |。Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.unmarshal_server_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5581a1d98b24b53aae0da674719c594de51a7bb7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="error-unable-to-initiate-dcom-communication"></a>エラー : DCOM 通信を初期化できません。
ローカル コンピューターがリモート コンピューターと通信しようとしたときに DCOM エラーが発生しました。 このエラーは、リモート サーバーのファイアウォール、またはリモート コンピューターで Windows 認証が破損していることに原因があります。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   リモート コンピューターに Windows ファイアウォールが有効になっている場合は、次を参照してください。[リモート デバッグ](../debugger/remote-debugging.md)ローカル デバッグのファイアウォールを構成する方法についてはします。  
  
-   Windows 認証を復元するために、両方のコンピューターを再起動してみます。 Kerberos エラーがないかどうかローカル コンピューターとリモート コンピューターのイベント ログを確認し、既知の問題がないかどうかドメイン管理者に問い合わせてください。  
  
## <a name="see-also"></a>関連項目  
 [Remote Debugging](../debugger/remote-debugging.md)