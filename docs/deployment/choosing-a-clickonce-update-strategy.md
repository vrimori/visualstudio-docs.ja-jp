---
title: ClickOnce の更新方法の選択 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application updates, ClickOnce
- updates, ClickOnce
- ClickOnce deployment, update strategies
ms.assetid: d8b6e7bb-4ea0-47f3-91cd-48580bdceccc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a4da8dddc667b032c6c284dc62197ff05a1a328f
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081798"
---
# <a name="choose-a-clickonce-update-strategy"></a>ClickOnce の更新方法を選択します。
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] では、アプリケーションを自動的に更新できます。 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションが定期的にアプリケーションの更新があるかどうかを確認するには、配置マニフェスト ファイルを読み取ります。 利用可能であれば、アプリケーションの新しいバージョンがダウンロードされて実行されます。 効率性を高めるために、変更されたファイルだけがダウンロードされます。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションのデザイン時に、アプリケーションが利用可能な更新プログラムをチェックする際に使用する方法を決定する必要があります。 使用できる基本的な方法は、アプリケーションの起動時に更新プログラムをチェックする方法、アプリケーションの起動後に更新プログラムをチェックする方法 (バックグラウンド スレッドで実行)、更新用のユーザー インターフェイスを提供する方法の 3 つです。  
  
 また、アプリケーションが更新プログラムをチェックする頻度を決定でき、更新を必須にすることもできます。  
  
> [!NOTE]
>  アプリケーションの更新には、ネットワーク接続が必要です。 ネットワーク接続されていない場合、選択した更新方法に関係なく、アプリケーションは更新プログラムをチェックせずに実行されます。  
  
> [!NOTE]
>  .NET Framework 2.0 と .NET Framework 3.0 では、いつでも、アプリケーションのチェック、更新プログラムの前に、または開始の後、またはを使用して、 \<xref:System.Deployment.Application > Api を設定する必要がある`deploymentProvider`配置マニフェストにします。 `deploymentProvider`要素は、対応する Visual Studio で、**の場所を更新**フィールドに、**更新**のダイアログ ボックス、**発行**タブ。この規則は .NET Framework 3.5 で緩和されています。 詳細については、次を参照してください。 [ClickOnce アプリケーションのテストの展開および Resigning なしの実稼働サーバー](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)します。  
  
## <a name="check-for-updates-after-application-startup"></a>アプリケーションの起動後の更新プログラムの確認  
 この方法を使用した場合、アプリケーションは、実行中にバックグラウンドで配置マニフェスト ファイルの検索と読み取りを試みます。 更新が利用可能な場合は、ユーザーが次回アプリケーションを実行したときに、更新プログラムをダウンロードしてインストールするかどうかを確認するプロンプトが表示されます。  
  
 この方法は、低帯域幅のネットワーク接続や、ダウンロードに時間を要する可能性のあるサイズの大きなアプリケーションに最も適しています。  
  
 この更新プログラム戦略を有効にするには、**アプリケーションの起動後**で、**アプリケーションの更新プログラムを確認する必要があります **のセクション、**アプリケーションの更新プログラム**ダイアログ ボックス。 セクションで、更新の間隔を指定**アプリケーションの更新プログラムを確認する頻度を指定**します。  
  
 これは、変更する場合と同じ、 **Update**展開内の要素は次のようにマニフェストします。  
  
```xml  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <expiration maximumAge="6" unit="hours" />  
   </update>  
</subscription>  
```  
  
## <a name="check-for-updates-before-application-startup"></a>アプリケーションの起動前に更新プログラムの確認  
 既定の方法では、アプリケーションが起動される前に、配置マニフェストの検索と読み取りが試みられます。 この方法を使用した場合、ユーザーがアプリケーションを起動するたびに、アプリケーションは配置マニフェスト ファイルの検索と読み取りを試みます。 更新プログラムが利用可能な場合は、更新プログラムがダウンロードされ、起動されます。それ以外の場合は、アプリケーションの既存のバージョンが起動されます。  
  
 この方法は、高帯域幅のネットワーク接続に最も適しています。低帯域幅の接続では、アプリケーション起動時の遅延が容認できないほど長くなる可能性があります。  
  
 この更新プログラム戦略を有効にするには、**アプリケーションを開始する前に**で、**アプリケーションの更新プログラムを確認する必要があります **のセクション、**アプリケーションの更新プログラム**ダイアログ ボックス。  
  
 これは、変更する場合と同じ、 **Update**展開内の要素は次のようにマニフェストします。  
  
```xml  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <beforeApplicationStartup />  
   </update>  
</subscription>  
```  
  
## <a name="make-updates-required"></a>必要な更新を行う  
 アプリケーションの最新バージョンを実行するようユーザーに要求することが必要な場合があります。 たとえば、Web サービスなどの外部リソースに変更を加えたことで、旧バージョンのアプリケーションが適切に動作できなくなるような場合です。 この場合、更新を必須としてマークし、ユーザーが旧バージョンを実行するのを防ぎます。  
  
> [!NOTE]
>  更新プログラムを要求するには、他の更新方法を使用して、チェック**アプリケーションを開始する前に**を以前のバージョンを実行できないことを保証する唯一の方法です。 起動時に必須の更新が検出された場合、ユーザーは更新を受け入れるか、アプリケーションを終了する必要があります。  
  
 必要な場合は、クリックとしてマークする**このアプリケーションの最低限必要なバージョン指定**で、**アプリケーション更新** ダイアログ ボックスし、発行バージョンを指定 (**メジャー**、**マイナー**、**ビルド**、**リビジョン**)、インストールできるアプリケーションの最も低いバージョン番号を指定します。  
  
 これは、設定と同じ、 **minimumRequiredVersion**の属性、**展開**に配置マニフェスト内の要素例。  
  
```xml  
<deployment install="true" minimumRequiredVersion="1.0.0.0">  
```  
  
## <a name="specify-update-intervals"></a>更新間隔を指定します。  
 アプリケーションが更新プログラムをチェックする頻度を指定できます。 そのためには、前の「アプリケーション起動後の更新プログラムのチェック」で説明したように、アプリケーションが起動後に更新プログラムをチェックするように指定します。  
  
 更新間隔を指定するには、設定、**アプリケーションの更新プログラムを確認する頻度を指定**プロパティで、**アプリケーションの更新プログラム** ダイアログ ボックス。  
  
 これは、設定と同じ、 **maximumAge**と**単位**の属性、 **Update**配置マニフェスト内の要素。  
  
 たとえば、アプリケーションを実行するたびにチェックしたり、週に 1 回または月に 1 回チェックしたりできます。 指定した時期にネットワーク接続されていない場合は、アプリケーションを次回実行したときに、更新プログラムのチェックが実行されます。  
  
## <a name="provide-a-user-interface-for-updates"></a>更新プログラムのユーザー インターフェイスを提供します。  
 この方法を使用する場合、アプリケーション開発者は、アプリケーションが更新プログラムをチェックする場所と頻度をユーザーが選択できるようにするユーザー インターフェイスを提供します。 たとえば、[更新を今すぐ確認] コマンドや、別の更新間隔を選択できる [更新の設定] ダイアログ ボックスなどを提供できます。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]配置 Api では、独自のユーザー インターフェイスの更新のプログラミングのフレームワークを提供します。 詳細については、「<xref:System.Deployment.Application>」を参照してください。  
  
 アプリケーションが配置 API を使用して自身の更新ロジックを制御する場合、次の「更新プログラムのチェックのブロッキング」で説明されているように更新プログラムのチェックをブロックする必要があります。  
  
 この方法は、ユーザーごとに異なる更新方法が必要な場合に最も適しています。  
  
## <a name="block-update-checking"></a>更新プログラムのチェックをブロックします。  
 アプリケーションが更新プログラムをチェックしないようにすることもできます。 たとえば、更新されることのない単純なアプリケーションがあるが、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] の配置によって提供されるインストールの容易さは利用したい場合があります。  
  
 更新プログラムのアプリケーションでは、配置 Api を使用して、独自の更新を実行する場合にチェックをブロックすることも必要があります。このトピックの「"更新プログラムのユーザー インターフェイスを提供する"を参照してください。  
  
 更新プログラムのチェックをブロックするには、オフ、**アプリケーションの更新プログラムを確認する必要があります**アプリケーションの更新プログラム ダイアログ ボックスのチェック ボックス。  
  
 配置マニフェストから `<Subscription>` タグを削除することにより、更新プログラムのチェックをブロックすることもできます。  
  
## <a name="permission-elevation-and-updates"></a>アクセス許可の昇格と更新プログラム  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションの新しいバージョンが、実行の際に以前のバージョンよりも高い信頼レベルを必要とする場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] はユーザーに対し、この高い信頼レベルをアプリケーションに付与するかどうかを確認します。 ユーザーが高い信頼レベルの付与を拒否した場合、更新プログラムはインストールされません。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] で、次回の起動時にアプリケーションを再インストールするように求めるメッセージが表示されます。 その時点でユーザーがより高い信頼レベルの付与を拒否し、更新が必須とマークされていない場合は、アプリケーションの古いバージョンが実行されます。 ただし、更新が必須である場合は、ユーザーがより高い信頼レベルを受け入れるまで、アプリケーションは実行されません。  
  
 信頼されたアプリケーションの配置を使用する場合は、信頼レベルの要求が行われません。 詳細については、次を参照してください。[信頼されたアプリケーション展開の概要](../deployment/trusted-application-deployment-overview.md)します。  
  
## <a name="see-also"></a>関連項目  
 \<xref:System.Deployment.Application >   
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce 配置ストラテジを選択します。](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [セキュリティで保護された ClickOnce アプリケーション](../deployment/securing-clickonce-applications.md)   
 [ClickOnce がアプリケーションの更新プログラムを実行する方法](../deployment/how-clickonce-performs-application-updates.md)   
 [方法: ClickOnce アプリケーションの更新プログラムの管理](../deployment/how-to-manage-updates-for-a-clickonce-application.md)