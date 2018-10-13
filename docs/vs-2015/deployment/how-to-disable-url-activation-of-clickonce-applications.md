---
title: '方法: ClickOnce アプリケーションの URL アクティべーションを無効にする |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 47fc07ade4529ab99a4c687ea62791ec083d2d0b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273332"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>方法 : ClickOnce アプリケーションの URL アクティべーションを無効にする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

通常、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] アプリケーションは Web サーバーからインストールされた直後に自動的に起動します。 セキュリティ上の理由から、この動作を無効にしてからアプリケーションを起動するユーザーに通知すること可能性があります、**開始** メニューの代わりにします。 次の手順では、URL アクティベーションを無効にする方法を説明します。  
  
 この手法は、Web サーバーからユーザーのコンピューターにインストールされた [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] アプリケーションにのみ使用できます。 URL を使用する方法でのみ起動できるオンライン専用のアプリケーションには使用できません。 アプリケーションとインストールされているオンライン専用アプリケーションの違いの詳細については、次を参照してください。 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)します。  
  
 この手順では、[!INCLUDE[winsdklong](../includes/winsdklong-md.md)] ツールである MageUI.exe を使用します。 このツールの詳細については、次を参照してください。 [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)します。 この手順は、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] を使用して実行することもできます。  
  
## <a name="procedure"></a>プロシージャ  
  
#### <a name="to-disable-url-activation-for-your-application"></a>アプリケーションの URL アクティベーションを無効にするには  
  
1.  MageUI.exe で配置マニフェストを開きます。 まだ作成していない 1 つ場合の手順に従います[チュートリアル: ClickOnce アプリケーションを手動で配置](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)します。  
  
2.  選択、**展開オプション**タブ。  
  
3.  クリア、**インストール後にアプリケーションを自動的に実行**チェック ボックスをオンします。  
  
4.  マニフェストを保存し、署名します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)



