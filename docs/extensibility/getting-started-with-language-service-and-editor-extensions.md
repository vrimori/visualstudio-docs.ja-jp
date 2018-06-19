---
title: 言語サービスとエディター拡張機能の概要 |Microsoft ドキュメント
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
ms.openlocfilehash: 5e36f4a6b0f8cb37a5ede782c24c7593285b7705
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131591"
---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>言語サービスとエディター拡張機能の概要
エディターの拡張機能を使用して、独自のプログラミング言語または任意のコンテンツ タイプをアウトライン表示、かっこの照合、IntelliSense、および電球などの言語サービス機能を追加することができます。 Visual Studio のエディター、色分け、余白、修飾、および他のビジュアル要素のテキストなどの動作と外観をカスタマイズすることもできます。 また、コンテンツの種類を定義でき、コンテンツが表示されるテキスト ビューの動作と外観を指定できます。  
  
 エディターの拡張機能の作成を開始するには、Visual Studio SDK の一部としてインストールされているエディター プロジェクト テンプレートを使用します。 Visual Studio SDK は、ダウンロード可能な一連の Vspackage を使用するか、Managed Extensibility Framework (MEF) を使用して、Visual Studio 拡張機能を開発するより簡単にするツールです。  
  
> [!NOTE]
>  Visual Studio SDK の詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)です。  
  
 独自のエディター拡張機能を記述する前に、次の概念とテクノロジについて学習することをお勧めします。  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) およびエディターの拡張機能  
 Visual Studio エディターのユーザー インターフェイス (UI) については、Windows Presentation Foundation (WPF) を使用して実装されます。 WPF では、豊富な視覚的効果とビジネス ロジックのコードの視覚的な側面を分離する一貫性のあるプログラミング モデルを提供します。 エディターの拡張機能を作成するときに、多くの WPF 要素と機能を使用できます。 詳細については、次を参照してください。 [Windows Presentation Foundation](/dotnet/framework/wpf/index)です。  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) およびエディターの拡張機能  
 Visual Studio エディターでは、Managed Extensibility Framework (MEF) を使用して、そのコンポーネントおよび拡張機能を管理します。 MEF では、開発者複数が簡単に Visual Studio と同様に、ホスト アプリケーションの拡張機能を作成することもできます。 このフレームワークでは、MEF コントラクトに従って拡張機能を定義し、MEF コンポーネントの一部としてエクスポートします。 ホスト アプリケーションは、検索することに、登録して、正しいコンテキストに適用されることを確認して、コンポーネント部分を管理します。  
  
> [!NOTE]
>  エディターで、MEF の詳細については、次を参照してください。[エディターでの Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)です。  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio エディターの拡張ポイントと拡張機能  
 エディターの拡張ポイントは、MEF コンポーネント パーツをカスタマイズして拡張することです。 場合によっては、拡張ポイントを拡張するインターフェイスを実装して、適切なメタデータと共にエクスポートすることによってです。 それ以外の場合だけ、拡張機能を宣言して特定の型としてエクスポートします。  
  
 基本的な種類のエディター拡張機能の一部を次に示します。  
  
-   マージンやスクロール バー  
  
-   Tags  
  
-   修飾  
  
-   オプション  
  
-   IntelliSense  
  
 エディターの拡張機能ポイントの詳細については、次を参照してください。[言語サービスとエディター拡張機能ポイント](../extensibility/language-service-and-editor-extension-points.md)です。  
  
## <a name="deploying-editor-extensions"></a>エディターの拡張機能の配置  
 Visual Studio では、source.extension.vsixmanifest をソリューションに、ソリューションの構築をという名前のメタデータ ファイルを追加し、Visual Studio に認識されているフォルダーにバイナリ ファイルとマニフェストのコピーを追加してエディター拡張機能を展開します。 マニフェスト ファイルでは、(たとえば、名前、作成者、バージョン、およびコンテンツの種類など) の拡張機能の基本的な情報を定義します。 VSIX マニフェスト ファイルと拡張機能を展開する方法の詳細については、次を参照してください。 [Visual Studio 拡張機能の配布](../extensibility/shipping-visual-studio-extensions.md)です。  
  
 コンピューターに拡張機能をインストールするときに、Visual Studio に認識されているフォルダーのサブフォルダーに、バイナリと、マニフェストを含めます。  
  
> [!WARNING]
>  Visual Studio に含まれているエディターの機能拡張テンプレートのいずれかを使用する場合に、マニフェストと配置場所の詳細について心配する必要はありません。 テンプレートには、登録および拡張機能を展開する必要があるすべてのものが含まれます。  
  
## <a name="running-extensions-in-the-experimental-instance"></a>実験用インスタンスで拡張機能を実行しています。  
 次の実験用フォルダー (Windows Vista および Windows 7) 上に展開することで、拡張機能を開発する際、作業バージョンの Visual Studio が分離されることができます。  
  
 *%Localappdata%* \VisualStudio\10.0Exp\Extensions\\*会社*\\*ExtensionID*  
  
 ここで *%localappdata%* 、ログオン ユーザーの名前を指定*会社*、拡張機能を所有している会社の名前を指定し、 *ExtensionID*拡張機能の id を指定します。  
  
 実験用の場所に拡張機能を配置する場合は、デバッグ モードで実行されます。 Visual Studio の 2 番目のインスタンスが開始され、名前は**Microsoft Visual Studio の実験用インスタンス**です。  
  
## <a name="managing-extensions"></a>拡張機能を管理します。  
 Visual Studio の拡張機能は、「**拡張機能と更新**(上、**ツール**メニュー). 実験用インスタンスで拡張機能をテストする場合に示さ**拡張機能と更新プログラム**実験用インスタンスの開発用のインスタンスには表示されませんが、します。  
  
 詳細については、「[Visual Studio 拡張機能の検索と使用](../ide/finding-and-using-visual-studio-extensions.md)」を参照してください。  
  
## <a name="using-templates-to-create-editor-extensions"></a>テンプレートを使用して、エディターの拡張機能を作成するには  
 エディターのテンプレートを使用すると、分類子、修飾、および余白をカスタマイズする MEF 拡張機能を作成します。 C# および Visual Basic の両方のプロジェクトのテンプレートがあります。 詳細については、次を参照してください。[エディター項目テンプレートに、拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
 VSIX プロジェクト テンプレートを使用して、拡張機能を作成することができますも。 このテンプレートは、任意の種類の拡張機能を展開しており、source.extension.vsixmanifest ファイル、必要なアセンブリ参照を展開できるようにビルド タスクを含むプロジェクト ファイルに必要な要素のみを提供します拡張機能です。 詳細については、次を参照してください。 [VSIX プロジェクト テンプレート](../extensibility/vsix-project-template.md)です。  
  
 作成することもエディター MEF コンポーネントを Visual Studio パッケージの拡張機能からです。 詳細については、次のチュートリアルを参照してください。  
  
-   [チュートリアル: エディター拡張機能でシェル コマンドを使用する](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [チュートリアル: エディター拡張機能でショートカット キーを使用する](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)