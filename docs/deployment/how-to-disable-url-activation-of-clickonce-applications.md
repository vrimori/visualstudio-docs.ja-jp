---
title: '方法: ClickOnce アプリケーションの URL アクティべーションを無効にする |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9ab9204513c59d2c853c0a3738ef2363739d56c1
ms.sourcegitcommit: 551f13774e8bb0eb47cbd973745628a956e866aa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2018
ms.locfileid: "49459622"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>方法: ClickOnce アプリケーションの URL アクティべーションを無効にします。

通常、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは Web サーバーからインストールされた直後に自動的に起動します。 セキュリティ上の理由から、この動作を無効にしてからアプリケーションを起動するユーザーに通知すること可能性があります、**開始** メニューの代わりにします。 次の手順では、URL アクティベーションを無効にする方法を説明します。

この手法は、Web サーバーからユーザーのコンピューターにインストールされた [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションにのみ使用できます。 URL を使用する方法でのみ起動できるオンライン専用のアプリケーションには使用できません。 アプリケーションとインストールされているオンライン専用アプリケーションの違いの詳細については、次を参照してください。 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)します。

この手順では、Windows ソフトウェア開発キット (SDK) ツールの MageUI.exe を使用します。 このツールの詳細については、次を参照してください。 [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)します。 Visual Studio を使用してこの手順を実行することもできます。

## <a name="procedure"></a>プロシージャ

### <a name="to-disable-url-activation-for-your-application"></a>アプリケーションの URL アクティベーションを無効にするには

1.  MageUI.exe で配置マニフェストを開きます。 まだ作成していない 1 つ場合の手順に従います[チュートリアル: ClickOnce アプリケーションを手動で展開](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)します。

2.  選択、**展開オプション**タブ。

3.  クリア、**インストール後にアプリケーションを自動的に実行**チェック ボックスをオンします。

4.  マニフェストを保存し、署名します。

## <a name="see-also"></a>関連項目

- [ClickOnce アプリケーションを発行します。](../deployment/publishing-clickonce-applications.md)