---
title: '方法: 配置の更新用の別の場所の指定 |Microsoft Docs'
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
ms.openlocfilehash: 76be049c670fb91911be70132b459cad5e5183bd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902465"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>方法: 配置の更新用の別の場所を指定します。
インストールすることができます、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] CD やファイル共有から最初にアプリケーションが、アプリケーションは、Web での定期的な更新プログラムを確認する必要があります。 その最初のインストール後に、Web からアプリケーションを更新できるように、配置マニフェストの更新プログラムの別の場所を指定できます。  
  
> [!NOTE]
>  アプリケーションは、この機能を使用するには、ローカルにインストールするように構成する必要があります。 詳細については、次を参照してください。[チュートリアル: ClickOnce アプリケーションを手動で展開](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)します。 さらに、インストールする場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]原因別の場所を設定、ネットワークからアプリケーション[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]最初のインストールとすべての後続の更新の両方にその場所を使用します。 (たとえば、CD など) からアプリケーションをローカルでインストールすると、元のメディアを使用して、最初のインストールを実行し、すべての後続の更新が別の場所を使用しています。  
  
### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>MageUI.exe (Windows フォーム ベースのユーティリティ) を使用して更新プログラムの別の場所を指定します。  
  
1.  .NET Framework コマンド プロンプトと種類を開きます。  
  
     **mageui.exe**  
  
2.  **ファイル**] メニューの [選択**開く**をアプリケーションの配置マニフェストを開きます。  
  
3.  選択、**展開オプション**タブ。  
  
4.  テキスト ボックスに名前付き**起動場所**アプリケーションの更新プログラムの配置マニフェストを含むディレクトリへの URL を入力します。  
  
5.  配置マニフェストを保存します。  
  
### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>Mage.exe を使用して更新プログラムの別の場所を指定します。  
  
1. .NET Framework コマンド プロンプトを開きます。  
  
2. 次のコマンドを使用して更新プログラムの場所を設定します。 この例で*HelloWorld.exe.application*へのパス、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]は .application という拡張子を持つ常に、アプリケーション マニフェストと*<http://adatum.com/Update/Path>* そのをURLには[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]はアプリケーションの更新プログラムを確認します。  
  
    **Mage-HelloWorld.exe.application ProviderUrl の更新 http://adatum.com/Update/Path**  
  
3. ファイルを保存します。  
  
   > [!NOTE]
   >  今すぐに使用して、ファイルを再署名する必要があります*Mage.exe*します。 詳細については、次を参照してください。[チュートリアル: ClickOnce アプリケーションを手動で展開](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)します。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 場合は、CD などのオフライン メディアから、アプリケーションをインストールして、コンピューターがオンラインで[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]で指定された URL はまず、`<deploymentProvider>`タグの最新のバージョンが更新プログラムの場所に含まれているかどうか、配置マニフェストで、アプリケーション。 その場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]の代わりに、最初のインストール ディレクトリから、そこから直接アプリケーションをインストールし、共通言語ランタイム (CLR) は、アプリケーションの信頼を決定します。 レベルを使用して`<deploymentProvider>`。 コンピューターがオフラインの場合、または`<deploymentProvider>`にアクセスできない[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]CD、および CLR からのインストールには、インストール ポイントに基づいて信頼が与えられます。 つまり CD インストールの場合、アプリケーションは完全な信頼を受け取ります。 すべての後続の更新では、その信頼レベルを継承します。  
  
 すべて[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]を使用するアプリケーション`<deploymentProvider>`アプリケーションが異なる別のコンピューターの信頼レベルを受け取らないようにするに、そのアプリケーション マニフェストで必要なアクセス許可を明示的に宣言する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: ClickOnce アプリケーションを手動で展開します。](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)   
 [セキュリティで保護された ClickOnce アプリケーション](../deployment/securing-clickonce-applications.md)   
 [ClickOnce の更新方法を選択します。](../deployment/choosing-a-clickonce-update-strategy.md)