---
title: "言語サービスとエディターの拡張機能の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
caps.latest.revision: 21
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 3cc009e23d123f50b108533e135bd51e123b3809
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>言語サービスとエディターの拡張機能の概要
エディターの拡張機能を使用すると、プログラミング言語または任意のコンテンツ タイプには、アウトライン表示、かっこの一致、IntelliSense、および電球などの言語サービス機能を追加します。 Visual Studio エディターの色分け、余白、表示要素、および他のビジュアル要素のテキストなどの動作と外観をカスタマイズすることもできます。 コンテンツの種類を定義し、コンテンツが表示されるテキスト ビューの動作と外観を指定できます。  
  
 エディターの拡張機能の作成を開始するには、Visual Studio SDK の一部としてインストールされているエディターのプロジェクト テンプレートを使用します。 Visual Studio SDK は、Vspackage を使用するか、Managed Extensibility Framework (MEF) を使用して、Visual Studio 拡張機能を開発するより簡単にするツールのダウンロード可能なセットです。  
  
> [!NOTE]
>  Visual Studio SDK の詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  
  
 独自のエディター拡張機能を記述する前に、次の概念とテクノロジについて学習することをお勧めします。  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) およびエディターの拡張機能  
 Visual Studio エディターのユーザー インターフェイス (UI) については、Windows Presentation Foundation (WPF) を使用して実装されます。 WPF では、豊富な視覚的効果と、コードの視覚的な側面をビジネス ロジックから分離する一貫性のあるプログラミング モデルを提供します。 エディターの拡張機能を作成するときに、多くの WPF 要素と機能を使用できます。 詳細については、次を参照してください。 [Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d)します。  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) およびエディターの拡張機能  
 Visual Studio エディターでは、そのコンポーネントおよび拡張機能を管理するのに Managed Extensibility Framework (MEF) を使用します。 MEF では、開発者の多く Visual Studio などのホスト アプリケーション用の拡張機能を簡単に作成することもできます。 このフレームワークでは、MEF コントラクトに従って拡張機能を定義し、MEF コンポーネントの一部としてエクスポートします。 ホスト アプリケーションは、発見して、登録、およびそれらが正しいコンテキストに適用されていることを確認して、コンポーネント パーツを管理します。  
  
> [!NOTE]
>  詳細については、MEF エディターで、次を参照してください。[エディターで Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)します。  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio エディターの拡張ポイントと拡張機能  
 エディターの拡張ポイントが MEF コンポーネントをカスタマイズおよび拡張することができます。 場合によっては、インターフェイスを実装して、適切なメタデータと共にエクスポートすることによって拡張ポイントを拡張します。 それ以外の場合にのみ拡張機能を宣言して特定の型としてエクスポートします。  
  
 基本的な種類のエディター拡張機能の一部を次に示します。  
  
-   余白とスクロール バー  
  
-   Tags  
  
-   表示要素  
  
-   オプション  
  
-   IntelliSense  
  
 エディターの拡張ポイントの詳細については、次を参照してください。[言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)します。  
  
## <a name="deploying-editor-extensions"></a>エディターの拡張機能を展開します。  
 Visual Studio では、ソリューションを構築、ソリューションに source.extension.vsixmanifest という名前のメタデータ ファイルを追加して、Visual Studio には、認識されているフォルダーにバイナリ ファイルとマニフェストのコピーを追加してエディター拡張機能を展開します。 マニフェスト ファイルでは、拡張機能 (たとえば、名前、作成者、バージョン、およびコンテンツの種類など) に関する基本的な情報を定義します。 VSIX のマニフェスト ファイルおよび拡張機能を展開する方法の詳細については、次を参照してください。 [Visual Studio 拡張機能の配布](../extensibility/shipping-visual-studio-extensions.md)します。  
  
 コンピューターで拡張機能をインストールするときに、Visual Studio に認識されているフォルダーのサブフォルダーに、バイナリ ファイルとマニフェストを含めます。  
  
> [!WARNING]
>  Visual Studio に含まれているエディターの機能拡張テンプレートのいずれかを使用する場合は、マニフェストと配置場所の詳細について心配する必要はありません。 テンプレートには、登録および拡張機能を展開するために必要ものが含まれています。  
  
## <a name="running-extensions-in-the-experimental-instance"></a>実験用インスタンスで拡張機能を実行しています。  
 (Windows Vista および Windows 7) で次の実験用のフォルダーに展開することによって拡張機能を開発する際、作業バージョンの Visual Studio を切り離すことができます。  
  
 *%Localappdata%*\VisualStudio\10.0Exp\Extensions\\*会社*\\*ExtensionID*  
  
 ここで*%localappdata%* 、ログオン ユーザーの名前を指定*会社*、拡張機能を所有している会社の名前を指定し、 *ExtensionID*拡張機能の id を指定します。  
  
 拡張機能を実験的な場所に配置するときは、デバッグ モードで実行します。 Visual Studio の&2; つ目のインスタンスが開始され、名前は**Microsoft Visual Studio の実験用インスタンス**します。  
  
## <a name="managing-extensions"></a>拡張機能を管理します。  
 Visual Studio の拡張機能は、「**拡張機能と更新プログラム**(上、**ツール**メニュー)。 実験用インスタンスで拡張機能をテストする場合に示さ**拡張機能と更新プログラム**実験用インスタンスですが開発用インスタンスで表示されていません。  
  
 詳細については、次を参照してください。 [Visual Studio 拡張機能の使用を検索および](../ide/finding-and-using-visual-studio-extensions.md)です。  
  
## <a name="using-templates-to-create-editor-extensions"></a>テンプレートを使用して、エディターの拡張機能を作成するには  
 エディターのテンプレートを使用すると、分類子、表示要素、および余白をカスタマイズする MEF 拡張機能を作成します。 C# および Visual Basic の両方のプロジェクトのテンプレートがあります。 詳細については、次を参照してください。[エディター項目テンプレートを使用して拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)します。  
  
 VSIX プロジェクト テンプレートを使用すると、拡張機能の作成もできます。 このテンプレートは、任意の種類の拡張機能を展開しており、source.extension.vsixmanifest ファイル、必要なアセンブリ参照、拡張機能を配置するためのビルド タスクを含むプロジェクト ファイルに必要な要素のみを提供します。 詳細については、次を参照してください。 [VSIX プロジェクトのテンプレート](../extensibility/vsix-project-template.md)します。  
  
 作成することもエディター MEF コンポーネントを Visual Studio パッケージの拡張機能からです。 詳細については、次のチュートリアルを参照してください。  
  
-   [チュートリアル: エディター拡張機能とシェル コマンドを使用します。](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [チュートリアル: エディター拡張機能とショートカット キーを使用します。](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)
