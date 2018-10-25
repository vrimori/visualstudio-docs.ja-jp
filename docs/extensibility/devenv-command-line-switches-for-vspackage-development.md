---
title: VSPackage 開発の Devenv コマンド ライン スイッチ |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
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
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8fd305133f913877f8d4ad4808a8c4efcab52af4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847059"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>VSPackage 開発の Devenv コマンド ライン スイッチ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] により、開発者は実行時に、コマンドラインからタスクを自動化する*devenv.exe*、Visual Studio 統合開発環境 (IDE) を開始するファイル。  

 タスクは次のとおりです。  

-   IDE の外部から定義済みの構成でアプリケーションを展開します。  

-   自動的にプリセットを使用してプロジェクトをビルドする設定を作成するかのデバッグ構成。  

-   IDE の外部からすべての特定の構成で IDE を読み込んでいます。 さらに、起動すると、IDE をカスタマイズできます。  

## <a name="guidelines-for-switches"></a>スイッチのガイドライン  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ドキュメントでは、ユーザー レベルの devenv コマンド ライン スイッチについて説明します。 詳細については、次を参照してください。 [Devenv コマンド ライン スイッチ](../ide/reference/devenv-command-line-switches.md)します。 Devenv には、VSPackage の開発、展開、およびデバッグで便利な追加のコマンド ライン スイッチもサポートしています。  


| コマンド ライン スイッチ | 説明 |
|---------------------| - |
| /safemode | 起動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]セーフ モードで、既定の IDE とサービスの読み込み。 /Safemode スイッチから読み込むときにすべてのサード パーティ Vspackage を防止する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]開始、安定した実行を確認します。<br /><br /> このスイッチは引数を取りません。 |
| /resetskippkgs | 問題の Vspackage の読み込みを回避するために必要のあるユーザーによって追加された読み込みのオプションをスキップすべて消去されますが、開始[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 SkipLoading タグの存在は、VSPackage の読み込みを無効にします。 VSPackage の読み込みを再度有効にタグをクリアします。<br /><br /> このスイッチは引数を取りません。 |
| /rootsuffix | 開始[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]別の場所を使用しています。 によって作成されたショートカットで、次のコマンドを実行、[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]インストーラー。<br /><br /> devenv/RootSuffix exp<br /><br /> この場合は、exp 10.0 ではなく、特定のサフィックス、たとえば 10.0Exp と場所を識別します。 実験用インスタンスでは、インスタンスから個別に VSPackage をデバッグできます。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コードを記述するを使用しています。<br /><br /> このスイッチは、VSRegEx.exe を使用して作成した場所を識別する任意の文字列を実行できます。 詳細については、次を参照してください。 [、実験用インスタンス](../extensibility/the-experimental-instance.md)します。 |
| /splash | 表示、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]スプラッシュ画面を通常どおりにし、メインの IDE を表示する前にメッセージ ボックスを表示します。 メッセージ ボックスを使用して、VSPackage 製品アイコンなどを確認する、スプラッシュ スクリーンを調査できます。<br /><br /> このスイッチは引数を取りません。 |

## <a name="see-also"></a>関連項目  
 [コマンド ライン スイッチを追加します。](../extensibility/adding-command-line-switches.md)   
 [Devenv コマンドライン スイッチ](../ide/reference/devenv-command-line-switches.md)