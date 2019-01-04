---
title: パッケージ化と SharePoint ソリューションの配置 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c1213d4dd2cdd347fe1d29f594fa7614df50b1e6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849020"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>パッケージ化し、SharePoint ソリューションのデプロイ
  通常、ソリューション パッケージ (.wsp) ファイルを使用して、SharePoint サーバーに SharePoint ソリューションをデプロイします。 Visual Studio を使用して機能に、SharePoint プロジェクト アイテムを整理して、SharePoint の機能を展開するパッケージを作成することができます。  
  
 ここでは、次の情報について説明します。  
  
-   [フィーチャーとパッケージの作成](#Creating)  
  
-   [機能およびツールのサポートをパッケージ化](#Tools)  
  
-   [SharePoint ソリューションの配置](#Deploying)  
  
-   [SharePoint ソリューション内のファイルを展開します。](#DeployingFiles)  
  
## <a name="create-features-and-packages"></a>フィーチャーとパッケージを作成します。
 Visual Studio を使用すると、グループに関連する SharePoint 要素、*機能*します。 たとえば、連絡先リスト定義の機能では、リスト インスタンスと、リスト定義を含めることができます。 配置用に 1 つの機能には、これら 2 つの要素を組み合わせることができます。 機能の詳細については、次を参照してください。[ビルディング ブロック。機能](http://go.microsoft.com/fwlink/?LinkID=169183)します。  
  
 次に、SharePoint ソリューション パッケージを作成することができます (*.wsp*) 複数の機能をバンドルするサイトの定義、アセンブリ、およびその他のファイルにファイルを配置する SharePoint に必要な形式で、ファイルを保存する 1 つのパッケージサーバー。 詳細については、次を参照してください。[ビルディング ブロック。ソリューション](http://go.microsoft.com/fwlink/?LinkID=169186)します。  
  
## <a name="feature-and-packaging-tool-support"></a>機能およびパッケージ化ツールのサポート
 Visual Studio での SharePoint 開発ツールを使用して、すばやく機能と展開が容易にソリューション パッケージに SharePoint ファイルを整理することができます。 フィーチャーとソリューションのパッケージを構成するのには、次のツールを使用できます。  
  
-   フィーチャー デザイナーとパッケージ デザイナー。  
  
-   パッケージング エクスプ ローラー、ツール ウィンドウです。  
  
-   ソリューション エクスプ ローラー。  
  
### <a name="feature-designer-and-package-designer"></a>フィーチャー デザイナーとパッケージ デザイナー
 フィーチャーを作成し、スコープを設定して、フィーチャー デザイナーを使用して、その他の機能を依存関係としてマークできます。 デザイナーには、各機能を説明する最終的な XML ファイルも表示されます。 詳細については、次を参照してください。[作成の SharePoint 機能](../sharepoint/creating-sharepoint-features.md)します。  
  
 特定の Web サイトまたは Web サイトのグループを設定して、機能を適用、*スコープ*フィーチャー デザイナーでします。 個々 の Web サイトの機能がアクティブの場合、この機能は、その特定の Web サイトでのみ機能します。 サイト コレクションの機能がアクティブの場合は、サイト全体のコレクションにフィーチャー内の項目が適用されます。 詳細については、次を参照してください。[要素スコープ](http://go.microsoft.com/fwlink/?LinkID=169189)します。  
  
 設定することができます、機能は、その他の機能に依存する場合、*機能のアクティブ化依存関係*機能を使用できるようにする前に、依存する機能をマークします。 かどうか、依存する機能がそのスコープに既にアクティブ化フィーチャーのアクティブ化依存関係を確認します。 詳細については、次を参照してください。[アクティブ化依存関係とスコープ](http://go.microsoft.com/fwlink/?LinkID=169190)します。  
  
 パッケージ デザイナーでは、SharePoint の要素を 1 つのソリューション パッケージにグループ化し、デプロイ時に、Web サーバーをリセットするかどうかを構成できます。 配置サーバーの種類を設定するには、使用、**プロパティ**ウィンドウ。 デザイナーには、パッケージの内容を記述する XML ファイルも生成されます。 詳細については、次を参照してください。[作成 SharePoint ソリューション パッケージ](../sharepoint/creating-sharepoint-solution-packages.md)します。  
  
 デプロイ時に、ソリューション ファイルを SharePoint サーバーにコピーする、インターネット インフォメーション サービス (IIS) サービスが停止しました。 Visual Studio のパッケージ デザイナーを使用すると、Web サーバーを再起動する必要があるかどうかを選択できます。 フロント エンド Web サーバーまたはアプリケーション サーバーに、ソリューションがデプロイされている場合を構成するを使用して、**プロパティ**ウィンドウ。 詳細については、次を参照してください。[ソリューションの要素 (ソリューション)](http://go.microsoft.com/fwlink/?LinkID=169191)します。  
  
### <a name="packaging-explorer"></a>パッケージング エクスプ ローラー  
 フィーチャー デザイナーとパッケージ デザイナーを補完するには、SharePoint ファイルをグループ化機能とパッケージをパッケージング エクスプ ローラーを使用できます。 さらに、パッケージ、フィーチャー、SharePoint プロジェクトの階層ビューを表示できる項目、およびファイルです。 パッケージング エクスプ ローラーは、次のタスクを完了するために使用できるツール ウィンドウです。  
  
- SharePoint プロジェクト項目とファイルを開きます。  
  
- ドラッグし、機能の 1 つから別の SharePoint プロジェクト アイテムを削除します。  
  
- ドラッグし、1 つのパッケージから SharePoint プロジェクト項目およびフィーチャーをドロップします。  
  
- パッケージに新しい機能を追加します。  
  
- フィーチャーまたはパッケージ デザイナーを開きます。  
  
- フィーチャーとパッケージを検証します。  
  
  Visual Studio での SharePoint 開発ツールでは、ソリューション パッケージの形式が正しく確保しやすく、検証規則があります。 さらに、ルールを確認する、 *.wsp*ソリューション ファイルを正常にデプロイおよび SharePoint サーバーでアクティブ化します。 機能の詳細については、XML スキーマは、次を参照してください。[機能スキーマ](http://go.microsoft.com/fwlink/?LinkID=169192)します。  
  
  SharePoint プロジェクト システムには、カスタムのフィーチャーとパッケージ検証規則を追加できます。 詳細については、「[方法 :SharePoint ソリューションの検証規則を使用したカスタムのフィーチャーとパッケージの作成](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)です。  
  
  パッケージング エクスプ ローラーの詳細については、次を参照してください。[方法。追加およびパッケージング エクスプ ローラーを使用して、フィーチャーおよびパッケージに項目を削除](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)します。  
  
### <a name="solution-explorer"></a>ソリューション エクスプローラー
 ソリューション エクスプ ローラーを使用して、移動し、SharePoint プロジェクトのファイルを開くことができます。 ソリューション エクスプ ローラーで、コンテキスト メニューを使用して、機能、フィーチャー イベント レシーバーを追加して、フィーチャーのリソース。 さらに、機能と展開のパッケージを構成するには、フィーチャー デザイナーとパッケージ デザイナーを開くことができます。  
  
## <a name="deploy-sharepoint-solutions"></a>SharePoint ソリューションを配置します。
 作成することができます、機能と Visual Studio でパッケージをカスタマイズした後、 *.wsp* SharePoint サーバーを展開するファイル。 デバッグし、テストを Visual Studio を使用することができます、します。*wsp*開発用コンピューターで SharePoint サーバー上でのみです。 リモート SharePoint サーバーに、SharePoint ソリューションをデプロイする方法の詳細については、次を参照してください。[ソリューションを展開する](http://go.microsoft.com/fwlink/?LinkID=169194)します。  
  
 開発用コンピューターでの展開手順をカスタマイズすることもできます。 詳細については、次を参照してください。[デプロイ、発行、および SharePoint ソリューション パッケージをアップグレード](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)します。  
  
## <a name="deploy-files-in-sharepoint-solutions"></a>ファイルの SharePoint ソリューションをデプロイします。
 通常、SharePoint ソリューションを SharePoint プロジェクト アイテムを追加するときに必要なすべてのファイルが含まれています。 可能性のあるファイルのコンパイル (コード ファイル)、ソリューションの出力アセンブリに組み込まれています。 ただし、非コンパイルのファイルを追加する必要がありますも *.xml*、 *.txt*、または SharePoint プロジェクトのリソース ファイル。 これらのファイルは、ソリューションに自動的にパッケージ化されません。 パッケージ化されることを確認するには、追加するか、ファイルまたは SharePoint プロジェクト項目にマップされたフォルダー。  
  
 マップされたフォルダーに追加されたファイルは、ソリューションのデプロイ時に自動的に SharePoint ハイブにコピーされます。 SharePoint プロジェクト アイテムに追加されたファイルがで指定されている場所に展開されている、**配置場所**、部分的に設定されている各ファイルのプロパティに基づいて、**展開の種類**プロパティ。 既定で、**展開の種類**プロパティの値が**NoDeployment**、ソリューション ファイルが展開されていないことを意味します。 ファイルをパッケージに含めるプロパティの別の値を設定する必要があります。  
  
 たとえば、追加するため、 *.xml*ファイルを SharePoint プロジェクトに、これらのアクションのいずれかを実行します。  
  
- SharePoint「レイアウト」マップされたフォルダーをプロジェクトに追加します。 これに作成**ソリューション エクスプ ローラー**という名前のフォルダー**レイアウト**プロジェクトのサブフォルダーを持ちます。 追加、 *.xml*新しいサブフォルダーにファイル。 既定では、ファイルは SharePoint のファイル システムの下に配置 *.\TEMPLATE\LAYOUTS\\\<フォルダー名 >* します。 マップされたフォルダーを追加する方法については、次を参照してください。[方法: 追加すると、マップされたフォルダーを削除する](../sharepoint/how-to-add-and-remove-mapped-folders.md)します。  
  
- 追加、 *.xml* 、SharePoint プロジェクト アイテムのフォルダーにファイルを開き、変更、**展開の種類**のプロパティ、 *.xml*ファイルから**NoDeployment**別設定などを**RootFile**または**ElementFile**します。 適切な**展開の種類**の設定、ファイルとプロジェクトに依存します。 詳細については、**展開の種類**プロパティの設定を参照してください[SharePoint の開発ソリューション](../sharepoint/developing-sharepoint-solutions.md)します。  
  
  ソリューションで特定のプロジェクトに追加したファイルが適用されない場合は、空の SharePoint プロジェクトをソリューションに追加し、し、その他のファイルを追加します。 コンテンツのデータベースに特に、sharepoint のファイルを展開するための別の方法として、プロジェクトにモジュールを追加し、モジュールにファイルを追加することです。 詳細については、次を参照してください。[モジュールを使用してファイルをソリューションに含める](../sharepoint/using-modules-to-include-files-in-the-solution.md)します。  
  
## <a name="see-also"></a>関連項目
 [SharePoint ソリューションを開発します。](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint ソリューションのビルドとデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
