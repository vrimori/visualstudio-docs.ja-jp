---
title: SharePoint ソリューション パッケージの作成 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0d275b7d2e4ccfea5d89148b6b46883fa32e6560
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53966665"
---
# <a name="create-sharepoint-solution-packages"></a>SharePoint ソリューション パッケージを作成します。
  配置パッケージを作成したりカスタマイズしたりするには、パッケージ デザイナーを使用します。 たとえば、SharePoint のプロジェクト項目およびフィーチャーの追加、IIS サーバーのリセット、フィーチャーのアクティブ化スコープの設定、フィーチャーの依存関係の特定などを行うことができます。 このデザイナーでは、マニフェスト (個々のパッケージを記述した XML ファイル) を生成することもできます。  
  
## <a name="packaging-tools"></a>パッケージ化ツール
 使用することができます、**パッケージ デザイナー**パッケージをカスタマイズし、マニフェストを生成します。 SharePoint のプロジェクト項目の追加、Web サーバーのリセットの構成、および配置用サーバーの種類の設定を行うことができます。 詳細については、「[方法 :追加して、パッケージ デザイナーを使用して機能と、パッケージにアイテムを削除](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)します。  
  
 また、使用することができます、**パッケージング エクスプ ローラー**機能およびパッケージ ファイル内の項目を変更する (*.wsp*)。 詳細については、「[方法 :追加およびパッケージング エクスプ ローラーを使用して、フィーチャーおよびパッケージに項目を削除](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)します。  
  
 パッケージを作成する Visual Studio および MSBuild を使用することができます (*.wsp*)、SharePoint ソリューションを配置するファイル。 SharePoint の配置に必要なマニフェスト ファイルはこのプロセスで生成されます。 詳細については、「[方法 :MSBuild タスクを使用した SharePoint ソリューション パッケージの作成](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)です。  
  
## <a name="package-designer-options"></a>パッケージ デザイナーのオプション
 次の表は、プロパティを持つ SharePoint パッケージでカスタマイズできること、**パッケージ デザイナー**します。  
  
|パッケージ デザイナーのプロパティ|既定の設定に関する説明|  
|-------------------------------|------------------------------------|  
|名前|必須。 パッケージの既定の名前に設定されて*ProjectName*します。|  
|[Web サーバーのリセット]|任意。 選択した後、Web サーバーを再起動する場合、 *.wsp*ファイル、SharePoint サーバーにインストールされます。|  
|配置サーバーの種類|必須。 既定では、スコープは ApplicationServer に設定されます。<br /><br /> アプリケーション サーバー:サービスをホストするサーバーを表します。<br /><br /> WebFrontEnd:Web サイトをホストするサーバーを表します。|  
|[ソリューション内の項目]|パッケージに追加できるすべての SharePoint プロジェクト項目およびフィーチャーを表します。|  
|[パッケージ内の項目]|任意。 パッケージ内の配置対象の SharePoint プロジェクト項目およびフィーチャーを表します。|  
  
## <a name="configure-the-packaging-process"></a>パッケージ化プロセスを構成します。
 Visual Studio で SharePoint ソリューションを開発した後、プロジェクトは、次のようにパッケージ化をカスタマイズできます。  
  
 次の表に、カスタマイズに使用できる 2 つの MSBuild ターゲットする方法、 *.wsp*ファイルが作成されます。  
  
|ターゲット|説明|  
|------------|-----------------|  
|BeforeLayout|ファイルが中間ディレクトリにコピーされる直前にタスクを実行するターゲット。 パッケージ ファイルを作成する前に、ファイルを変更することができます (*.wsp*)。|  
|AfterLayout|ファイルが中間ディレクトリにコピーされた直後にタスクを実行するターゲット。|  
  
 詳細については、[方法。MSBuild ターゲットを使用して SharePoint ソリューション パッケージをカスタマイズする](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)します。  
  
## <a name="packaging-architecture"></a>パッケージ化のアーキテクチャ
 SharePoint パッケージを作成するときに、次の手順が発生する (*.wsp*) Visual Studio でします。  
  
1.  パッケージの物理構造と意味構造が正しいことを確認するために、フィーチャーおよびパッケージが検証されます。  
  
2.  パッケージ内のフィーチャー、プロジェクト項目、およびパッケージ ファイルが列挙されます。 パッケージおよびフィーチャーのマニフェスト ファイルが変換されて、配置およびアクティブ化に必要な情報がすべて追加されます。 トークンは完全修飾値に置き換えられます。  
  
3.  カスタマイズ可能な BeforeLayout MSBuild ターゲットが実行されます。 前に、パッケージにカスタム変更を加えるには、この手順を作成することができます、 *.wsp*ファイルが作成されます。  
  
4.  列挙されたファイルが中間ディレクトリにコピーされます。  
  
5.  カスタマイズ可能な AfterLayout MSBuild ターゲットが実行されます。 前に、パッケージにカスタム変更を加えるには、この手順を作成することができます、 *.wsp*ファイルが作成されます。  
  
6.  中間ディレクトリにファイルに追加されます、 *.wsp*ファイル。  
  
## <a name="package-folder-structure"></a>パッケージ フォルダーの構造
 SharePoint プロジェクトをパッケージ化するとき、 *.wsp*でファイルを作成、 *SolutionFolder\bin\\\<BuildConfiguration >* フォルダー。 たとえば、ソリューションが*C:\Visual Studio 2013 \projects\listdefinition1*のリリースにビルド構成を設定し、 *.wsp*ファイルにある*C:\Visual Studio 2013\Projects\ListDefinition1\bin\Release*します。  
  
## <a name="see-also"></a>関連項目
 [方法: SharePoint ソリューション パッケージをカスタマイズします。](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [方法: 追加して、パッケージ デザイナーを使用して機能と、パッケージにアイテムを削除](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)   
 [方法: MSBuild タスクを使用した SharePoint ソリューション パッケージの作成します。](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [方法: MSBuild タスクを使用した SharePoint ソリューション パッケージの作成します。](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [方法: MSBuild ターゲットを使用して SharePoint ソリューション パッケージをカスタマイズします。](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)  
