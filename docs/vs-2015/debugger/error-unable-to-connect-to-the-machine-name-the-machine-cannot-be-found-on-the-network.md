---
title: 'エラー: マシンに接続できません&lt;名前&gt;します。 ネットワーク上にコンピューターが見つかりません。 | Microsoft Docs'
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
- vs.debug.remote.dcom_disabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4e2c60723827466942ea02b8881f234e38fa438
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223082"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>エラー: マシンに接続できません&lt;名前&gt;します。 ネットワーク上にコンピューターが見つかりません。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このエラーは、次の条件のいずれかが満たされると発生します。  
  
-   リモート コンピューターへの接続が解除された。  
  
-   リモート コンピューターのユーザー アカウントが無効になっている。  
  
-   リモート コンピューターのパスワードの有効期限が切れている。  
  
### <a name="to-resolve-this-behavior"></a>この問題を解決するには  
  
-   ローカル コンピューターとリモート コンピューターが同じネットワーク上に存在することを確認します。 これを行うには、Microsoft Windows エクスプローラー (ファイル エクスプローラー) を使用してリモート コンピューターにアクセスしてみます。  
  
     および  
  
-   リモート コンピューターへの接続に使用しているユーザー アカウントが有効になっていることを確認します。  
  
     および  
  
-   リモート コンピューターへの接続に使用しているパスワードが有効であり、有効期限が切れていないことを確認します。  
  
## <a name="see-also"></a>関連項目  
 [デバイスのリモート ツールをセットアップします。](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)



