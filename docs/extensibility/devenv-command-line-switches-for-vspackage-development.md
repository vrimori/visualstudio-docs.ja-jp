---
title: "Devenv コマンド ライン スイッチ VSPackage 開発 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
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
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ae42f7dd48a240f3d1c06c814834bc83c0cce75d
ms.lasthandoff: 02/22/2017

---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>VSPackage 開発の Devenv コマンド ライン スイッチ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]開発者は、devenv.exe、Visual Studio 統合開発環境 (IDE) を開始するファイルを実行するときに、コマンドラインからタスクを自動化できます。  
  
 タスクは次のとおりです。  
  
-   IDE の外部から定義済みの構成でアプリケーションを展開します。  
  
-   自動的にプリセットを使用してプロジェクトのビルドを使用するか、設定をビルド、デバッグ構成します。  
  
-   IDE の外部からすべての特定の構成で IDE を読み込んでいます。 さらに、起動すると、IDE をカスタマイズできます。  
  
## <a name="guidelines-for-switches"></a>スイッチのガイドライン  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ドキュメントでは、ユーザー レベル devenv コマンド ライン スイッチについて説明します。 詳細については、次を参照してください。 [Devenv コマンド ライン スイッチ](../ide/reference/devenv-command-line-switches.md)します。 Devenv には、VSPackage 開発、展開、およびデバッグで便利な追加のコマンド ライン スイッチもサポートしています。  
  
|コマンド ライン スイッチ|説明|  
|--------------------------|-----------------|  
|/safemode|起動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]セーフ モードで、既定の IDE とサービスだけをロードします。 /Safemode スイッチ vspackage すべてサード パーティ製を読み込まない場合[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]開始、実行を安定したを確認します。<br /><br /> このスイッチは引数を取りません。|  
|起動時|問題のある Vspackage が読み込まれないようにしたいユーザーによって追加された読み込みのオプションをスキップすべてをクリアし、開始[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 SkipLoading タグの存在は、VSPackage の読み込みを無効にします。 VSPackage の読み込みを再度有効にタグをオフにするとします。<br /><br /> このスイッチは引数を取りません。|  
|/rootsuffix|開始[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]別の場所を使用しています。 によって作成されたショートカットで、次のコマンドを実行、[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]インストーラー。<br /><br /> devenv/RootSuffix exp<br /><br /> この場合は、exp 関数は、10.0 ではなく、特定のサフィックス 10.0Exp 次に例を使用している場所を識別します。 実験用インスタンスでは、デバッグのインスタンスとは切り離して VSPackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コードの記述を使用しています。<br /><br /> このスイッチは、VSRegEx.exe を使用して作成した場所を識別する任意の文字列を取得できます。 詳細については、次を参照してください。[の実験用インスタンス](../extensibility/the-experimental-instance.md)します。|  
|/splash|表示、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]スプラッシュ画面を通常どおりにし、メインの IDE を表示する前に、メッセージ ボックスを表示します。 メッセージ ボックスを使用して、VSPackage 製品アイコンを次に例を確認すると、スプラッシュ画面を調査できます。<br /><br /> このスイッチは引数を取りません。|  
  
## <a name="see-also"></a>関連項目  
 [コマンド ライン スイッチを追加します。](../extensibility/adding-command-line-switches.md)   
 [Devenv コマンド ライン スイッチ](../ide/reference/devenv-command-line-switches.md)
