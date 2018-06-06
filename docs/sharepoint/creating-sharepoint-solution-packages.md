---
title: SharePoint ソリューション パッケージの作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: 957789c4adfc476429179ed84f87f544c0d37143
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765272"
---
# <a name="create-sharepoint-solution-packages"></a>SharePoint ソリューション パッケージを作成します。
  配置パッケージを作成したりカスタマイズしたりするには、パッケージ デザイナーを使用します。 たとえば、SharePoint のプロジェクト項目およびフィーチャーの追加、IIS サーバーのリセット、フィーチャーのアクティブ化スコープの設定、フィーチャーの依存関係の特定などを行うことができます。 このデザイナーでは、マニフェスト (個々のパッケージを記述した XML ファイル) を生成することもできます。  
  
## <a name="packaging-tools"></a>パッケージ化ツール
 使用することができます、**パッケージ デザイナー**パッケージをカスタマイズし、マニフェストを生成します。 SharePoint のプロジェクト項目の追加、Web サーバーのリセットの構成、および配置用サーバーの種類の設定を行うことができます。 詳細については、次を参照してください。[する方法: して追加および削除のフィーチャーおよび項目をパッケージにパッケージ デザイナーを使用して](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)です。  
  
 また、使用することができます、**パッケージング エクスプ ローラー**機能およびパッケージ ファイル内の項目を変更する (*.wsp*)。 詳細については、次を参照してください。[する方法: して追加および削除のフィーチャーおよび項目をパッケージにパッケージング エクスプ ローラーを使用して](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)です。  
  
 パッケージを作成する Visual Studio および MSBuild を使用することができます (*.wsp*)、SharePoint ソリューションを配置するファイル。 SharePoint の配置に必要なマニフェスト ファイルはこのプロセスで生成されます。 詳細については、次を参照してください。[する方法: SharePoint のパッケージを作成する](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)と[する方法: MSBuild タスクを使用して SharePoint ソリューション パッケージを作成](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)です。  
  
## <a name="package-designer-options"></a>パッケージ デザイナーのオプション
 次の表は、プロパティを含む SharePoint パッケージでカスタマイズできる、**パッケージ デザイナー**です。  
  
|パッケージ デザイナーのプロパティ|既定の設定に関する説明|  
|-------------------------------|------------------------------------|  
|name|必須。 パッケージの既定の名前に設定されている*ProjectName*です。|  
|[Web サーバーのリセット]|任意。 選択した後、Web サーバーを再起動する場合、 *.wsp*ファイルは、SharePoint サーバーにインストールします。|  
|配置サーバーの種類|必須。 既定では、スコープは ApplicationServer に設定されます。<br /><br /> ApplicationServer:、サービスをホストするサーバーがについて説明します。<br /><br /> WebFrontEnd:、Web サイトをホストするサーバーがについて説明します。|  
|[ソリューション内の項目]|パッケージに追加できるすべての SharePoint プロジェクト項目およびフィーチャーを表します。|  
|[パッケージ内の項目]|任意。 パッケージ内の配置対象の SharePoint プロジェクト項目およびフィーチャーを表します。|  
  
## <a name="configure-the-packaging-process"></a>パッケージ化プロセスを構成します。
 Visual Studio での SharePoint ソリューションを開発した後、プロジェクトをパッケージ化する方法をカスタマイズできます。  
  
 次の表に、カスタマイズに使用できる 2 つの MSBuild ターゲットが、どのように *.wsp*ファイルを作成します。  
  
|ターゲット|説明|  
|------------|-----------------|  
|BeforeLayout|ファイルが中間ディレクトリにコピーされる直前にタスクを実行するターゲット。 パッケージ ファイルを作成する前に、ファイルを変更することができます (*.wsp*)。|  
|AfterLayout|ファイルが中間ディレクトリにコピーされた直後にタスクを実行するターゲット。|  
  
 詳細については、[する方法: MSBuild のターゲットを使用して SharePoint ソリューション パッケージをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)です。  
  
## <a name="packaging-architecture"></a>パッケージ化のアーキテクチャ
 SharePoint パッケージを作成するときに発生する、次の手順 (*.wsp*) Visual Studio でします。  
  
1.  パッケージの物理構造と意味構造が正しいことを確認するために、フィーチャーおよびパッケージが検証されます。  
  
2.  パッケージ内のフィーチャー、プロジェクト項目、およびパッケージ ファイルが列挙されます。 パッケージおよびフィーチャーのマニフェスト ファイルが変換されて、配置およびアクティブ化に必要な情報がすべて追加されます。 トークンは完全修飾値に置き換えられます。  
  
3.  カスタマイズ可能な BeforeLayout MSBuild ターゲットが実行されます。 前にパッケージにカスタム変更を加えるには、このステップを作成することができます、 *.wsp*ファイルを作成します。  
  
4.  列挙されたファイルが中間ディレクトリにコピーされます。  
  
5.  カスタマイズ可能な AfterLayout MSBuild ターゲットが実行されます。 前にパッケージにカスタム変更を加えるには、このステップを作成することができます、 *.wsp*ファイルを作成します。  
  
6.  中間ディレクトリでファイルに追加されます、 *.wsp*ファイル。  
  
## <a name="package-folder-structure"></a>パッケージ フォルダーの構造
 SharePoint プロジェクト、パッケージ化するとき、 *.wsp*でのファイルが作成、 *SolutionFolder\bin\{BuildConfiguration}* フォルダーです。 たとえば、ソリューションが*C:\Visual Studio 2013\Projects\ListDefinition1*リリースに、ビルド構成が設定されていると、 *.wsp*ファイルにある*C:\Visual Studio 2013\Projects\ListDefinition1\bin\Release*です。  
  
## <a name="see-also"></a>関連項目
 [方法: SharePoint ソリューション パッケージをカスタマイズする](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [方法: して追加および削除のフィーチャーおよび項目をパッケージにパッケージ デザイナーの使用](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)   
 [方法: SharePoint パッケージの作成](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)   
 [方法: MSBuild タスクを使用して SharePoint ソリューション パッケージを作成します。](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [方法: MSBuild ターゲットを使用して SharePoint ソリューション パッケージをカスタマイズする](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)  
  
 