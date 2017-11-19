---
title: "Devenv コマンド ライン スイッチの VSPackage の開発 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /setup command line switch
- /resetskippkgs command line switch
- /noVSIP command line switch
- /rootsuffix command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ca93d63236eb1b50663eff4c86a6ae3603600802
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>VSPackage の開発の Devenv コマンド ライン スイッチ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]devenv.exe、Visual Studio 統合開発環境 (IDE) を開始するファイルを実行するときに、コマンドラインからタスクを自動化することができます。  
  
 タスクは次のとおりです。  
  
-   IDE の外部から定義済みの構成にアプリケーションを展開します。  
  
-   自動的にプリセットを使用してプロジェクトをビルドするはビルド設定や、構成のデバッグします。  
  
-   IDE の外部からすべての特定の構成で IDE を読み込んでいます。 さらの起動時に IDE をカスタマイズすることができます。  
  
## <a name="guidelines-for-switches"></a>スイッチのガイドライン  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ドキュメントでは、ユーザー レベル devenv コマンド ライン スイッチについて説明します。 詳細については、次を参照してください。 [Devenv コマンド ライン スイッチ](../ide/reference/devenv-command-line-switches.md)です。 Devenv には、VSPackage の開発、配置、およびデバッグで便利な追加のコマンド ライン スイッチもサポートしています。  
  
|コマンド ライン スイッチ|説明|  
|--------------------------|-----------------|  
|/safemode|起動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]セーフ モードで、既定の IDE とサービスの読み込みします。 /Safemode スイッチすべて vspackage サード パーティ製を読み込むときに[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]起動すると、実行を安定したを確認します。<br /><br /> このスイッチは引数を取りません。|  
|/resetskippkgs|開始し、問題のある Vspackage は、の負荷がかからないようにユーザーによって追加された読み込みのオプションをスキップすべてをクリア[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 SkipLoading タグの存在は、VSPackage の読み込みを無効にします。 VSPackage の読み込みを再度有効にタグをクリアします。<br /><br /> このスイッチは引数を取りません。|  
|/rootsuffix|開始[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]別の場所を使用しています。 によって作成されたショートカットで、次のコマンドを実行、[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]インストーラー。<br /><br /> devenv/RootSuffix exp<br /><br /> この場合、exp は 10.0 ではなく、特定のサフィックス、たとえば 10.0Exp と場所を識別します。 実験用インスタンスでは、インスタンスから個別に VSPackage をデバッグすることができます[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コードを記述するを使用しています。<br /><br /> このスイッチは、VSRegEx.exe を使用して作成した場所を識別する任意の文字列を受け取ることができます。 詳細については、次を参照してください。 [、実験用インスタンス](../extensibility/the-experimental-instance.md)です。|  
|/splash|表示、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]スプラッシュ画面を通常どおりにし、メインの IDE を表示する前に、メッセージ ボックスを表示します。 メッセージ ボックスを使用して、VSPackage の製品の アイコンの例を確認する、スプラッシュ スクリーンを調査できます。<br /><br /> このスイッチは引数を取りません。|  
  
## <a name="see-also"></a>関連項目  
 [コマンド ライン スイッチを追加します。](../extensibility/adding-command-line-switches.md)   
 [Devenv コマンド ライン スイッチ](../ide/reference/devenv-command-line-switches.md)