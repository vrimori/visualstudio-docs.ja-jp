---
title: 'エラー: リモートのコンピューターは DCOM 通信を初期化できませんでした。Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 79548e2fbfbb4c10ce912ab90cd0541aea7f1200
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547631"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>エラー : リモート コンピューターは DCOM 通信を初期化できませんでした。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[エラー: リモート コンピューターは DCOM 通信を開始できませんでした](https://docs.microsoft.com/visualstudio/debugger/error-remote-computer-could-not-initiate-dcom-communications)します。  
  
リモート コンピューターがローカル コンピューターと通信しようとしたときに DCOM エラーが発生しました。 ローカル コンピューターは、  
  
 Visual Studio を実行しているコンピューターです。 このエラーが発生する原因は複数あります。  
  
-   ローカル マシンのファイアウォールが有効になっていない。  
  
-   リモート マシンからローカル マシンへの Windows 認証が機能していない。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  ローカル コンピューターの Windows ファイアウォールが有効にされている場合は、次を参照してください。[設定 Up the Remote Tools のデバイスで](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)ローカル デバッグのファイアウォールを構成する方法についてはします。  
  
2.  リモート サーバーからローカル コンピューターのファイル共有を開いてみて Windows 認証をテストします。  
  
3.  Windows 認証を復元するために、両方のコンピューターを再起動してみます。 Kerberos エラーがないかどうかローカル コンピューターとリモート コンピューターのイベント ログを確認し、既知の問題がないかどうかドメイン管理者に問い合わせてください。  
  
## <a name="see-also"></a>関連項目  
 [デバイスのリモート ツールのセットアップ](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)



