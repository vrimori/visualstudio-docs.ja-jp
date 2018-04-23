---
title: ClickOnce の更新方法の選択 |Microsoft ドキュメント
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
ms.openlocfilehash: 0013b9f7ae004b709a1651af0e32e36dd45f909c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="choosing-a-clickonce-update-strategy"></a>ClickOnce の更新方法の選択
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] では、アプリケーションを自動的に更新できます。 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションは、アプリケーションの更新が使用できるかどうかを確認するには、配置マニフェスト ファイルを定期的に読み取ります。 利用可能であれば、アプリケーションの新しいバージョンがダウンロードされて実行されます。 効率性を高めるために、変更されたファイルだけがダウンロードされます。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションのデザイン時に、アプリケーションが利用可能な更新プログラムをチェックする際に使用する方法を決定する必要があります。 使用できる基本的な方法は、アプリケーションの起動時に更新プログラムをチェックする方法、アプリケーションの起動後に更新プログラムをチェックする方法 (バックグラウンド スレッドで実行)、更新用のユーザー インターフェイスを提供する方法の 3 つです。  
  
 また、アプリケーションが更新プログラムをチェックする頻度を決定でき、更新を必須にすることもできます。  
  
> [!NOTE]
>  アプリケーションの更新には、ネットワーク接続が必要です。 ネットワーク接続されていない場合、選択した更新方法に関係なく、アプリケーションは更新プログラムをチェックせずに実行されます。  
  
> [!NOTE]
>  .NET Framework 2.0 および .NET Framework 3.0 で、アプリケーションの起動の前後または <xref:System.Deployment.Application> の API を使用する前後に更新プログラムがあるかどうかをチェックする場合は、配置マニフェストで `deploymentProvider` を設定する必要があります。 `deploymentProvider`要素は、Visual studio に対応しています、**の場所を更新**フィールドに、**更新**のダイアログ ボックス、**発行**タブです。この規則は .NET Framework 3.5 で緩和されています。 詳細については、次を参照してください。 [ClickOnce アプリケーションのテスト用の展開および Resigning なしの実稼働サーバー](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)です。  
  
## <a name="checking-for-updates-after-application-startup"></a>アプリケーション起動後の更新プログラムのチェック  
 この方法を使用した場合、アプリケーションは、実行中にバックグラウンドで配置マニフェスト ファイルの検索と読み取りを試みます。 更新が利用可能な場合は、ユーザーが次回アプリケーションを実行したときに、更新プログラムをダウンロードしてインストールするかどうかを確認するプロンプトが表示されます。  
  
 この方法は、低帯域幅のネットワーク接続や、ダウンロードに時間を要する可能性のあるサイズの大きなアプリケーションに最も適しています。  
  
 この更新方法を有効にする] をクリックして**アプリケーションの起動後**で、**アプリケーションの更新プログラムを確認する必要があります [**のセクションで、**アプリケーションの更新プログラム**ダイアログ ボックス。 セクションで、更新の間隔を指定**アプリケーションが更新プログラムを確認する頻度を指定して**です。  
  
 これは、変更した場合と同じ、**更新**マニフェストの次のように、展開内の要素。  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <expiration maximumAge="6" unit="hours" />  
   </update>  
</subscription>  
```  
  
## <a name="checking-for-updates-before-application-startup"></a>アプリケーション起動前の更新プログラムのチェック  
 既定の方法では、アプリケーションが起動される前に、配置マニフェストの検索と読み取りが試みられます。 この方法を使用した場合、ユーザーがアプリケーションを起動するたびに、アプリケーションは配置マニフェスト ファイルの検索と読み取りを試みます。 更新プログラムが利用可能な場合は、更新プログラムがダウンロードされ、起動されます。それ以外の場合は、アプリケーションの既存のバージョンが起動されます。  
  
 この方法は、高帯域幅のネットワーク接続に最も適しています。低帯域幅の接続では、アプリケーション起動時の遅延が容認できないほど長くなる可能性があります。  
  
 この更新方法を有効にする] をクリックして**アプリケーションを開始する前に**で、**アプリケーションの更新プログラムを確認する必要があります [**のセクション、**アプリケーションの更新プログラム**ダイアログ ボックス。  
  
 これは、変更した場合と同じ、**更新**マニフェストの次のように、展開内の要素。  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <beforeApplicationStartup />  
   </update>  
</subscription>  
```  
  
## <a name="making-updates-required"></a>更新の必須化  
 アプリケーションの最新バージョンを実行するようユーザーに要求することが必要な場合があります。 たとえば、Web サービスなどの外部リソースに変更を加えたことで、旧バージョンのアプリケーションが適切に動作できなくなるような場合です。 この場合、更新を必須としてマークし、ユーザーが旧バージョンを実行するのを防ぎます。  
  
> [!NOTE]
>  更新を要求するには、他の更新方法を使用して、オン**アプリケーションを開始する前に**を古いバージョンを実行できないことを保証する唯一の方法です。 起動時に必須の更新が検出された場合、ユーザーは更新を受け入れるか、アプリケーションを終了する必要があります。  
  
 必要な場合は、クリックとしてマークする**このアプリケーションに最低限必要なバージョンを指定**で、**アプリケーション更新** ダイアログ ボックス、および発行バージョンを指定 (**メジャー**、**マイナー**、**ビルド**、**リビジョン**) をインストールできるアプリケーションの最も低いバージョン番号を指定します。  
  
 これは、設定と同じ、 **minimumRequiredVersion**の属性、**展開**配置マニフェスト内の要素例。  
  
```  
<deployment install="true" minimumRequiredVersion="1.0.0.0">  
```  
  
## <a name="specifying-update-intervals"></a>更新間隔の指定  
 アプリケーションが更新プログラムをチェックする頻度を指定できます。 そのためには、前の「アプリケーション起動後の更新プログラムのチェック」で説明したように、アプリケーションが起動後に更新プログラムをチェックするように指定します。  
  
 更新間隔を指定するには、設定、**アプリケーションが更新プログラムを確認する頻度を指定**内のプロパティ、**アプリケーションの更新プログラム** ダイアログ ボックス。  
  
 これは、設定と同じ、 **maximumAge**と**単位**の属性、**更新**配置マニフェスト内の要素。  
  
 たとえば、アプリケーションを実行するたびにチェックしたり、週に 1 回または月に 1 回チェックしたりできます。 指定した時期にネットワーク接続されていない場合は、アプリケーションを次回実行したときに、更新プログラムのチェックが実行されます。  
  
## <a name="providing-a-user-interface-for-updates"></a>更新プログラム用ユーザー インターフェイスの提供  
 この方法を使用する場合、アプリケーション開発者は、アプリケーションが更新プログラムをチェックする場所と頻度をユーザーが選択できるようにするユーザー インターフェイスを提供します。 たとえば、[更新を今すぐ確認] コマンドや、別の更新間隔を選択できる [更新の設定] ダイアログ ボックスなどを提供できます。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]配置 Api では、独自のユーザー インターフェイスの更新のプログラミングのフレームワークを提供します。 詳細については、「<xref:System.Deployment.Application>」を参照してください。  
  
 アプリケーションが配置 API を使用して自身の更新ロジックを制御する場合、次の「更新プログラムのチェックのブロッキング」で説明されているように更新プログラムのチェックをブロックする必要があります。  
  
 この方法は、ユーザーごとに異なる更新方法が必要な場合に最も適しています。  
  
## <a name="blocking-update-checking"></a>更新プログラムのチェックのブロッキング  
 アプリケーションが更新プログラムをチェックしないようにすることもできます。 たとえば、更新されることのない単純なアプリケーションがあるが、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] の配置によって提供されるインストールの容易さは利用したい場合があります。  
  
 アプリケーションが配置 API を使用して自身の更新を実行する場合も、更新プログラムのチェックをブロックする必要があります。前の「更新用ユーザー インターフェイスの提供」を参照してください。  
  
 更新プログラムのチェックをブロックするには、クリア、**アプリケーションの更新プログラムを確認する必要があります**アプリケーションの更新 ダイアログ ボックスにチェック ボックスをオンします。  
  
 配置マニフェストから `<Subscription>` タグを削除することにより、更新プログラムのチェックをブロックすることもできます。  
  
## <a name="permission-elevation-and-updates"></a>アクセス許可の昇格と更新  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションの新しいバージョンが、実行の際に以前のバージョンよりも高い信頼レベルを必要とする場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] はユーザーに対し、この高い信頼レベルをアプリケーションに付与するかどうかを確認します。 ユーザーが高い信頼レベルの付与を拒否した場合、更新プログラムはインストールされません。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] で、次回の起動時にアプリケーションを再インストールするように求めるメッセージが表示されます。 その時点でユーザーがより高い信頼レベルの付与を拒否し、更新が必須とマークされていない場合は、アプリケーションの古いバージョンが実行されます。 ただし、更新が必須である場合は、ユーザーがより高い信頼レベルを受け入れるまで、アプリケーションは実行されません。  
  
 信頼されたアプリケーションの配置を使用する場合は、信頼レベルの要求が行われません。 詳細については、「 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Deployment.Application>   
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)   
 [ClickOnce がアプリケーションの更新プログラムを実行する方法](../deployment/how-clickonce-performs-application-updates.md)   
 [方法 : ClickOnce アプリケーションの更新プログラムを管理する](../deployment/how-to-manage-updates-for-a-clickonce-application.md)