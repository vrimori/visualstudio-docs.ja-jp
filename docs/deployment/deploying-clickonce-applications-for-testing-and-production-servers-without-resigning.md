---
title: "再署名を行わない ClickOnce アプリケーションの配置 (テスト サーバーおよび運用サーバー) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "アプリケーションの更新プログラム, ClickOnce"
  - "ClickOnce アプリケーション, 配置 (再署名なしで)"
  - "ClickOnce 配置, 再署名なしで"
  - "deploymentProvider タグ"
  - "マニフェスト [ClickOnce]"
  - "更新プログラムの場所 [ClickOnce]"
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 再署名を行わない ClickOnce アプリケーションの配置 (テスト サーバーおよび運用サーバー)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このトピックでは、.NET Framework Version 3.5 で導入された ClickOnce の新機能について説明します。この機能を使用すると、ClickOnce マニフェストに再署名したり、ClickOnce マニフェストを変更したりせずに、ネットワーク上の複数の場所から ClickOnce アプリケーションを配置できます。  
  
> [!NOTE]
>  新しいバージョンのアプリケーションを配置する場合には、従来どおり、再署名を行う方法が推奨されます。  可能な限り、再署名を行う方法を採用してください。  詳細については、「[Mage.exe \(マニフェストの生成および編集ツール\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)」を参照してください。  
  
 サードパーティの開発者と ISV は、この機能を選択し、ユーザーがアプリケーションを容易に更新できるようにすることが可能です。  この機能を使用できるシナリオについて、次に説明します。  
  
-   アプリケーションを \(初めてインストールするのではなく\) 更新する場合。  
  
-   コンピューター上にアプリケーションが 1 つだけ構成されている場合   \(たとえば、アプリケーションが 2 つの異なるデータベースを参照している場合、この機能は使用できません\)。  
  
## 配置マニフェストからの deploymentProvider の除外  
 .NET Framework 2.0 および .NET Framework 3.0 では、オフライン機能を利用できるシステムにインストールされている ClickOnce アプリケーションは、その配置マニフェストに `deploymentProvider` を指定する必要があります。  `deploymentProvider` は、"更新プログラムの場所" と呼ばれることもあり、ClickOnce がアプリケーションの更新プログラムをチェックする場所を指します。  配置に署名するためにアプリケーション発行者に求められる要件に加えて、この要件があることで、販売元などのサードパーティが ClickOnce アプリケーションを更新することを困難にしていました。  また、同じネットワーク上にある複数の場所から 1 つのアプリケーションを配置することも困難でした。  
  
 .NET Framework 3.5 の ClickOnce に加えられた変更により、サードパーティが別の組織に対して ClickOnce アプリケーションを提供し、さらに独自のネットワークにアプリケーションを配置することができるようになります。  
  
 この機能を利用するには、ClickOnce アプリケーションの開発者は、配置マニフェストから `deploymentProvider` を除外する必要があります。  これは、Mage.exe を使用して配置マニフェストを作成する場合は、`-providerUrl` 引数を除外することを意味します。MageUI.exe を使用して配置マニフェストを生成する場合は、**アプリケーション マニフェスト** タブの **\[開始場所\]** ボックスを空白のままにすることを意味します。  
  
## deploymentProvider とアプリケーションの更新プログラム  
 .NET Framework 3.5 以降では、ClickOnce アプリケーションをオンラインとオフラインで使用できるように配置するために、配置マニフェストに `deploymentProvider` を指定する必要はなくなりました。  これにより、配置をパッケージ化して署名する必要があるけれども、他の企業で自らのネットワーク上にアプリケーションを配置できるようにする、というシナリオがサポートされます。  
  
 `deploymentProvider` を除外したアプリケーションは、`deploymentProvider` タグを含む更新プログラムを提供しない限り、更新中にインストール場所を変更できないという点について注意する必要があります。  
  
 2 つの例を挙げて、この点について説明します。  まず、`deploymentProvider` タグを含まない ClickOnce アプリケーションを発行し、http:\/\/www.adatum.com\/MyApplication\/ からインストールを行うようにユーザーに依頼する場合を考えます。  アプリケーションの次の更新プログラムを http:\/\/subdomain.adatum.com\/MyApplication\/ から発行することを決めた場合、http:\/\/subdomain.adatum.com\/MyApplication\/ にある配置マニフェストに更新プログラムの署名を行う方法はありません。  この場合、次のいずれかを実行できます。  
  
-   ユーザーに対し、以前のバージョンをアンインストールし、新しい場所から新しいバージョンをインストールするように伝えます。  
  
-   http:\/\/www.adatum.com\/MyApplication\/ を参照する `deploymentProvider` を含めて、http:\/\/www.adatum.com\/MyApplication\/ に更新プログラムをいったん置きます。  その後、http:\/\/subdomain.adatum.com\/MyApplication\/ を参照する `deploymentProvider` を指定した別の更新プログラムをリリースします。  
  
 2 番目の例では、`deploymentProvider` を指定した ClickOnce アプリケーションを発行し、それを削除することにします。  `deploymentProvider` を含まない新しいバージョンをクライアントがダウンロードすると、`deploymentProvider` を含むバージョンのアプリケーションをリリースしない限り、更新プログラムに使用するパスにリダイレクトすることはできません。  最初に挙げた例と同様に、`deploymentProvider` は、最初は新しい場所ではなく、現在の更新プログラムの場所を指しています。  この場合、http:\/\/subdomain.adatum.com\/MyApplication\/ を参照する `deploymentProvider` を挿入しようとすると、次の更新は失敗します。  
  
## 配置の作成  
 異なるネットワーク上の場所から配置可能な配置を作成する手順については、「[チュートリアル : 再署名が不要で商標を保持する ClickOnce アプリケーションの手動配置](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)」を参照してください。  
  
## 参照  
 [Mage.exe \(マニフェストの生成および編集ツール\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(マニフェスト生成および編集ツールのグラフィカル クライアント\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)