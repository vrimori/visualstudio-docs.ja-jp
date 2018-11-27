---
title: 'エラー: ターゲット コンピューターに Visual Studio リモート デバッガー サービスはこのコンピューターに接続することはできません |Microsoft Docs'
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
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 89ecf99d-66bf-4da0-a840-aa95b0be1702
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f1e457829f7b6ab5050a02bd8f20e1c51d5df14
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798470"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>エラー : 対象コンピューター上の Visual Studio リモート デバッガーが、このコンピューターに接続できません。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このエラーは、Visual Studio リモート デバッガー サービスがデバッグを開始したコンピューターに接続するときに、このサービスを実行しているユーザー アカウントを認証できないことを示します。  
  
 コンピューターにアクセスできるアカウントは、次の表のとおりです。  
  
|||||  
|-|-|-|-|  
||LocalSystem アカウント|ドメイン アカウント|両方のコンピューターに同じユーザー名とパスワードを持つローカル アカウント|  
|両方のコンピューターが同じドメインにある場合|はい|[はい]|はい|  
|両方のコンピューターが双方向の信頼関係を持つドメインにある場合|いいえ|×|はい|  
|一方または両方のコンピューターがワークグループにある場合|いいえ|×|はい|  
|コンピューターが異なるドメインにある場合|いいえ|×|はい|  
  
 また、次の条件を満たす必要があります。  
  
-   Visual Studio リモート デバッガー サービスを実行するアカウントは、すべてのプロセスをデバッグできるように、リモート コンピューターの管理者アカウントであることが必要です。  
  
-   アカウントにも許可するが、`Log on as a service`を使用しているリモート コンピューター上の特権、**ローカル セキュリティ ポリシー**管理ツールです。  
  
-   ローカル アカウントを使用してコンピューターにアクセスしている場合は、ローカル アカウントで Visual Studio リモート デバッガー サービスを実行する必要があります。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  リモート コンピューターに Visual Studio リモート デバッガー サービスが正しく設定されていることを確認します。 詳細については、次を参照してください。[設定 Up the Remote Tools のデバイスで](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)します。  
  
2.  上の表に示した、デバッガー ホスト コンピューターにアクセスできる適切なアカウントを使用して、リモート デバッガー サービスを実行します。  
  
### <a name="to-add-log-on-as-a-service-privilege"></a>"サービスとしてログオンする" 特権を追加するには  
  
1.  **開始** メニューの 選択**コントロール パネルの **します。  
  
2.  コントロール パネルで、次のように選択します。**クラシック表示**、必要な場合。  
  
3.  **［管理ツール］** をダブルクリックします。  
  
4.  管理ツール ウィンドウでダブルクリック**ローカル セキュリティ ポリシー**します。  
  
5.  **ローカル セキュリティ設定**ウィンドウで、展開、**ローカル ポリシー**フォルダー。  
  
6.  クリックして**ユーザー権利の割り当て**します。  
  
7.  **ポリシー**列をダブルクリック**サービスとしてログオン**で現在のローカル グループ ポリシーの割り当てを表示する、**サービスとしてログオン** ダイアログ ボックス。  
  
8.  新しいユーザーを追加する をクリックして、**追加のユーザーまたはグループ**ボタンをクリックします。  
  
9. ユーザーの追加が完了したら、クリックして**OK**します。  
  
### <a name="to-work-around-this-error"></a>このエラーを回避するには  
  
-   リモート デバッグ モニターをサービスとして実行する代わりに、アプリケーションとして実行します。  
  
## <a name="see-also"></a>関連項目  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



