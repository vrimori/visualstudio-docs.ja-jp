---
title: '方法: 配置の更新用の別の場所の指定 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 14c6778d5cad698e6eea541b94df6f8eb793746c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>方法 : 配置の更新用に別の場所を指定する
インストールすることができます、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] CD またはファイル共有から最初にアプリケーションが、アプリケーションが、Web で定期的な更新プログラムのチェックが必要です。 その最初のインストール後に Web サイトからアプリを更新できるように、配置マニフェストで更新プログラムの別の場所を指定できます。  
  
> [!NOTE]
>  アプリケーションは、この機能を使用してローカルにインストールするように構成する必要があります。 詳細については、次を参照してください。[チュートリアル: ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)です。 また、インストールする場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]原因別の場所を設定、ネットワークからアプリケーション[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]最初のインストールと後続のすべての更新の両方の場所を使用します。 (たとえば、CD からアプリケーションをローカルでをインストールする場合、元のメディアを使用して最初のインストールを実行および以降の更新が別の場所を使用します。  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>MageUI.exe (Windows フォーム ベースのユーティリティ) を使用して更新プログラムの別の場所を指定します。  
  
1.  開き、.NET Framework コマンド プロンプトの種類。  
  
     **mageui.exe**  
  
2.  **ファイル**] メニューの [選択**開く**を開くには、アプリケーションの配置マニフェスト。  
  
3.  選択、**展開オプション**タブです。  
  
4.  テキスト ボックスに名前付き**場所の起動**アプリケーションの更新プログラムの配置マニフェストを格納するディレクトリに、URL を入力します。  
  
5.  配置マニフェストを保存します。  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Mage.exe を使用して更新プログラムの別の場所を指定します。  
  
1.  .NET Framework コマンド プロンプトを開きます。  
  
2.  次のコマンドを使用して更新プログラムの場所を設定します。 この例では**HelloWorld.exe.application**へのパス、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]は .application という拡張子を持つ常に、アプリケーション マニフェストと**http://adatum.com/Update/Path**そのをURLには[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]はアプリケーションの更新プログラムを確認します。  
  
     **Mage-HelloWorld.exe.application ProviderUrl の更新 http://adatum.com/Update/Path**  
  
3.  ファイルを保存します。  
  
    > [!NOTE]
    >  Mage.exe を使用してファイルを再署名する必要があります。 詳細については、次を参照してください。[チュートリアル: ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)です。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 場合は、CD などのオフラインの中から、アプリケーションをインストールして、コンピューターがオンラインで[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]で指定された URL はまず、`<deploymentProvider>`のより新しいバージョンが更新プログラムの場所に含まれているかどうか、配置マニフェスト内のタグ、アプリケーション。 場合は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]の代わりに、最初のインストール ディレクトリから、そこから直接アプリケーションをインストールし、共通言語ランタイム (CLR)、アプリケーションの信頼を決定するレベルを使用して`<deploymentProvider>`です。 場合は、コンピューターがオフライン、または`<deploymentProvider>`接続できず、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] CD、および CLR からのインストールには、インストール ポイントに基づく信頼が与えられます。 つまり CD インストールの場合は、完全な信頼をアプリケーションで受信します。 以降の更新では、その信頼レベルを継承します。  
  
 すべて[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]を使用するアプリケーション`<deploymentProvider>`アプリケーションが異なる別のコンピューター上の信頼レベルを受信しないようにに、そのアプリケーション マニフェストで必要な権限を明示的に宣言する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル : ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)   
 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)