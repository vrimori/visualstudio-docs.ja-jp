---
title: 'エラー: リモートのコンピューターは DCOM 通信を初期化できませんでした。Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 59c4be18adc854e326b8e756399818d46ba469ad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237927"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>エラー : リモート コンピューターは DCOM 通信を初期化できませんでした。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



