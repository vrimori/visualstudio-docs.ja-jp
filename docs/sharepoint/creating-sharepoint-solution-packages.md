---
title: "SharePoint ソリューション パッケージの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
ms.assetid: 6b1f1fbf-fa9c-453d-80af-36ec9829677a
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f21356c34a94540d20be2bb9fa092bff270f1a70
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="creating-sharepoint-solution-packages"></a>SharePoint ソリューション パッケージの作成
  配置パッケージを作成したりカスタマイズしたりするには、パッケージ デザイナーを使用します。 たとえば、SharePoint のプロジェクト項目およびフィーチャーの追加、IIS サーバーのリセット、フィーチャーのアクティブ化スコープの設定、フィーチャーの依存関係の特定などを行うことができます。 このデザイナーでは、マニフェスト (個々のパッケージを記述した XML ファイル) を生成することもできます。  
  
## <a name="packaging-tools"></a>パッケージ化ツール  
 使用することができます、**パッケージ デザイナー**パッケージをカスタマイズし、マニフェストを生成します。 SharePoint のプロジェクト項目の追加、Web サーバーのリセットの構成、および配置用サーバーの種類の設定を行うことができます。 詳細については、次を参照してください。[する方法: して追加および削除のフィーチャーおよび項目をパッケージにパッケージ デザイナーを使用して](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)です。  
  
 また、使用することができます、**パッケージング エクスプ ローラー**機能およびパッケージ ファイル (.wsp) 内の項目を変更します。 詳細については、次を参照してください。[する方法: して追加および削除のフィーチャーおよび項目をパッケージにパッケージング エクスプ ローラーを使用して](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)です。  
  
 SharePoint ソリューションを配置するためのパッケージ (.wsp) ファイルは、Visual Studio および MSBuild を使用して作成できます。 SharePoint の配置に必要なマニフェスト ファイルはこのプロセスで生成されます。 詳細については、次を参照してください。[する方法: SharePoint のパッケージを作成する](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)と[する方法: MSBuild タスクを使用して SharePoint ソリューション パッケージを作成](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)です。  
  
## <a name="package-designer-options"></a>パッケージ デザイナーのオプション  
 次の表は、プロパティを含む SharePoint パッケージでカスタマイズできる、**パッケージ デザイナー**です。  
  
|パッケージ デザイナーのプロパティ|既定の設定に関する説明|  
|-------------------------------|------------------------------------|  
|名前|必須です。 パッケージの既定の名前に設定されている*ProjectName*です。|  
|[Web サーバーのリセット]|省略可能です。 SharePoint サーバーに .wsp ファイルがインストールされた後に Web サーバーを再起動する場合に選択します。|  
|配置サーバーの種類|必ず指定します。 既定では、スコープは ApplicationServer に設定されます。<br /><br /> ApplicationServer:、サービスをホストするサーバーがについて説明します。<br /><br /> WebFrontEnd:、Web サイトをホストするサーバーがについて説明します。|  
|[ソリューション内の項目]|パッケージに追加できるすべての SharePoint プロジェクト項目およびフィーチャーを表します。|  
|[パッケージ内の項目]|省略可能です。 パッケージ内の配置対象の SharePoint プロジェクト項目およびフィーチャーを表します。|  
  
## <a name="configuring-the-packaging-process"></a>パッケージ化処理の構成  
 Visual Studio での SharePoint ソリューションを開発した後、プロジェクトをパッケージ化する方法をカスタマイズできます。  
  
 次の表に、.wsp ファイルの作成方法をカスタマイズするために使用できる 2 つの MSBuild ターゲットを示します。  
  
|ターゲット|説明|  
|------------|-----------------|  
|BeforeLayout|ファイルが中間ディレクトリにコピーされる直前にタスクを実行するターゲット。 パッケージ ファイル (.wsp) を作成する前に、ファイルに変更を加えることができます。|  
|AfterLayout|ファイルが中間ディレクトリにコピーされた直後にタスクを実行するターゲット。|  
  
 詳細については、[する方法: MSBuild のターゲットを使用して SharePoint ソリューション パッケージをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)です。  
  
## <a name="packaging-architecture"></a>パッケージ化のアーキテクチャ  
 Visual Studio で SharePoint パッケージ (.wsp) を作成すると、次のステップが実行されます。  
  
1.  パッケージの物理構造と意味構造が正しいことを確認するために、フィーチャーおよびパッケージが検証されます。  
  
2.  パッケージ内のフィーチャー、プロジェクト項目、およびパッケージ ファイルが列挙されます。 パッケージおよびフィーチャーのマニフェスト ファイルが変換されて、配置およびアクティブ化に必要な情報がすべて追加されます。 トークンは完全修飾値に置き換えられます。  
  
3.  カスタマイズ可能な BeforeLayout MSBuild ターゲットが実行されます。 このステップを設けることによって、.wsp ファイルの作成前に、パッケージに独自の変更を適用することができます。  
  
4.  列挙されたファイルが中間ディレクトリにコピーされます。  
  
5.  カスタマイズ可能な AfterLayout MSBuild ターゲットが実行されます。 このステップを設けることによって、.wsp ファイルの作成前に、パッケージに独自の変更を適用することができます。  
  
6.  中間ディレクトリのファイルが .wsp ファイルに追加されます。  
  
## <a name="package-folder-structure"></a>パッケージ フォルダーの構造  
 SharePoint プロジェクトをパッケージ化するときに .wsp ファイルが作成された、SolutionFolder\bin\\*BuildConfiguration*フォルダーです。 たとえば、ソリューションが*ドライブ*: \Visual Studio 2013\Projects\ListDefinition1 とビルド構成に設定されているリリース、.wsp ファイルにある*ドライブ*: \Visual Studio 2013\Projects\ListDefinition1\bin\Release です。  
  
## <a name="see-also"></a>関連項目  
 [方法: SharePoint ソリューション パッケージをカスタマイズする](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [方法: して追加および削除のフィーチャーおよび項目をパッケージにパッケージ デザイナーの使用](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)   
 [方法: SharePoint パッケージの作成](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)   
 [方法: MSBuild タスクを使用して SharePoint ソリューション パッケージを作成します。](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [方法: MSBuild ターゲットを使用して SharePoint ソリューション パッケージをカスタマイズする](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)  
  
  