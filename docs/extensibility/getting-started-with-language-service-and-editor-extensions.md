---
title: 言語サービスとエディターの拡張機能の概要 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c07d2f374890d6a87b5fe45304d098acfb05065b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498381"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>言語サービスとエディターの拡張機能を概要します。
エディター拡張機能を使用して、独自のプログラミング言語または任意のコンテンツ タイプをアウトライン表示、かっこの照合、IntelliSense、および電球などの言語サービスの機能を追加することができます。 テキストの色指定、余白、表示要素、および他のビジュアル要素など、Visual Studio エディターの動作と外観をカスタマイズすることもできます。 また、独自の種類のコンテンツを定義して、コンテンツが表示されるテキスト ビューの動作と外観を指定できます。  
  
 エディターの拡張機能の記述を開始するするには、Visual Studio SDK の一部としてインストールされているエディターのプロジェクト テンプレートを使用します。 Visual Studio SDK は、ダウンロード可能な一連の Vspackage を使用するか、Managed Extensibility Framework (MEF) を使用して、Visual Studio 拡張機能を開発するより簡単にするツールです。  
  
> [!NOTE]
>  Visual Studio SDK の詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  
  
 独自のエディター拡張機能を記述する前に、次の概念とテクノロジについて学習することをお勧めします。  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) とエディターの拡張機能  
 Visual Studio エディターのユーザー インターフェイス (UI) は、Windows Presentation Foundation (WPF) を使用して実装されます。 WPF では、豊富なビジュアル エクスペリエンスとビジネス ロジックからコードの視覚的な側面を分離する一貫したプログラミング モデルを提供します。 エディター拡張機能を作成するときに、多くの WPF 要素と機能を使用できます。 詳細については、次を参照してください。 [Windows Presentation Foundation](/dotnet/framework/wpf/index)します。  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) とエディターの拡張機能  
 Visual Studio エディターでは、そのコンポーネントおよび拡張機能を管理するのに Managed Extensibility Framework (MEF) を使用します。 MEF では、開発者の詳細について Visual Studio などのホスト アプリケーション用の拡張機能を簡単に作成することもできます。 このフレームワークは、MEF コントラクトに従って拡張機能を定義し、MEF コンポーネントの一部としてエクスポートします。 ホスト アプリケーションは、これらを検索するには、登録、それらが正しいコンテキストに適用されていることを確認して、コンポーネント部分を管理します。  
  
> [!NOTE]
>  エディターで、MEF の詳細については、次を参照してください。[エディターでの Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)します。  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio エディターの拡張ポイントと拡張機能  
 エディターの拡張ポイントは、MEF コンポーネント パーツをカスタマイズして拡張することができます。 場合によっては、拡張機能ポイントを拡張するインターフェイスを実装し、適切なメタデータと共にエクスポートすること。 それ以外の場合だけ拡張機能を宣言し、特定の型としてエクスポートします。  
  
 基本的な種類のエディター拡張機能の一部を次に示します。  
  
-   余白とスクロール バー  
  
-   Tags  
  
-   修飾  
  
-   オプション  
  
-   IntelliSense  
  
 エディターの拡張ポイントの詳細については、次を参照してください。[言語サービスとエディターの拡張機能ポイント](../extensibility/language-service-and-editor-extension-points.md)します。  
  
## <a name="deploying-editor-extensions"></a>エディターの拡張機能の配置  
 Visual Studio で、という名前のメタデータ ファイルを追加することでエディター拡張機能を展開する*source.extension.vsixmanifest*をソリューションに、ソリューションのビルドと呼ばれるフォルダーにバイナリ ファイルとマニフェストのコピーを追加Visual studio。 マニフェスト ファイルは、拡張機能 (たとえば、名前、作成者、バージョン、およびコンテンツの種類など) に関する基本的な情報を定義します。 VSIX のマニフェスト ファイルと拡張機能をデプロイする方法の詳細については、次を参照してください。[出荷 Visual Studio 拡張機能](../extensibility/shipping-visual-studio-extensions.md)します。  
  
 コンピューターで拡張機能をインストールするときに、Visual Studio に認識されているフォルダーのサブフォルダーにバイナリと、マニフェストを含めます。  
  
> [!WARNING]
>  Visual Studio に含まれているエディター拡張機能テンプレートのいずれかを使用する場合は、マニフェストと配置場所の詳細について心配する必要はありません。 テンプレートには、登録して、拡張機能をデプロイするために必要なすべてのものが含まれます。  
  
## <a name="run-extensions-in-the-experimental-instance"></a>実験用インスタンスで拡張機能を実行します。  
 (Windows Vista および Windows 7) の次の実験的なフォルダーに展開し、拡張機能を開発する際に、Visual Studio の作業バージョンを隔離できます。  
  
 *{%LOCALAPPDATA%}\VisualStudio\10.0Exp\Extensions\\{会社}\\{ExtensionID}*  
  
 場所 *%localappdata%* 、ログオン ユーザーの名前を指定*会社*、拡張機能を所有している会社の名前を指定し、 *ExtensionID*拡張機能の ID です。  
  
 実験的な場所に拡張機能を展開するときに、デバッグ モードで実行されます。 Visual Studio の 2 番目のインスタンスが開始され、名前は**Microsoft Visual Studio の実験用インスタンス**します。  
  
## <a name="manage-extensions"></a>拡張機能を管理します。  
 Visual Studio の拡張機能が記載されて**拡張機能と更新**(上、**ツール**メニュー)。 実験用インスタンスで拡張機能をテストする場合に表示されます**拡張機能と更新**、実験用インスタンスでは開発インスタンスで記載されていません。  
  
 詳細については、次を参照してください。[を検索し、Visual Studio 拡張機能を使用して、](../ide/finding-and-using-visual-studio-extensions.md)します。  
  
## <a name="use-templates-to-create-editor-extensions"></a>テンプレートを使用して、エディターの拡張機能を作成するには  
 エディター テンプレートを使用すると、分類子、表示要素、および余白をカスタマイズする MEF 拡張機能を作成します。 C# および Visual Basic の両方のプロジェクト テンプレートがあります。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能を作成する](../extensibility/creating-an-extension-with-an-editor-item-template.md)します。  
  
 拡張機能を作成するのに VSIX プロジェクト テンプレートを使用することもできます。 このテンプレートは、任意の種類の拡張機能を展開し、含めるに必要な要素のみを提供します、 *source.extension.vsixmanifest*ファイル、必要なアセンブリ参照、およびビルド タスクを含むプロジェクト ファイル。拡張機能をデプロイすることができます。 詳細については、次を参照してください。 [VSIX プロジェクト テンプレート](../extensibility/vsix-project-template.md)します。  
  
 作成することもエディター MEF コンポーネント Visual Studio パッケージの拡張機能から。 詳細については、次のチュートリアルを参照してください。  
  
-   [チュートリアル: エディター拡張機能でシェル コマンドを使用します。](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [チュートリアル: エディター拡張機能とショートカット キーの使用](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)