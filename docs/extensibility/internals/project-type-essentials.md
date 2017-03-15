---
title: "プロジェクトの種類の Essentials |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: 11
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
ms.openlocfilehash: 77ac7852a4fe42e69602edcd7e75354b404e315e
ms.lasthandoff: 02/22/2017

---
# <a name="project-type-essentials"></a>プロジェクトの種類の基本事項
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]などの言語のいくつかのプロジェクトの種類が含まれている[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]または[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]です。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]また、独自のプロジェクトの種類を作成してできます。  
  
 カスタム コマンド、エディター、またはツール ウィンドウを追加するだけの場合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、新しいプロジェクトの種類を作成しなくても実行できます。 詳細については、次のトピックを参照してください。  
  
-   [コマンド、メニューのおよびツールバー](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
-   [エディターと言語サービスの拡張機能](../../extensibility/editor-and-language-service-extensions.md)  
  
-   [拡張とカスタマイズ ツール ウィンドウ](../../extensibility/extending-and-customizing-tool-windows.md)  
  
 同様を指定された動作をカスタマイズするかどうかは[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]と[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]プロジェクトの種類で行うことができますプロジェクトのサブタイプを使用しています。 詳細については、次を参照してください。[プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)します。  
  
 以外の言語に基づくプロジェクトの新しいプロジェクトの種類を作成する必要があります[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]と[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]次の&1; つ以上をサポートする場合。  
  
-   ビルド  
  
-   配置  
  
-   複数の構成  
  
-   ソース管理  
  
-   デバッグ  
  
-   ソリューション エクスプ ローラーでプロジェクト項目  
  
-   **プロジェクトを開く**または**新しいプロジェクト**ダイアログ ボックス  
  
-   プロジェクトの入れ子  
  
-   プロジェクトの種類の機能に関する詳細については、次を参照してください。  
  
-   プロジェクトの種類は一連のインターフェイスを実装するオブジェクトは VSPackage で[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]が必要です。 を使用する C# の場合、プロジェクトの種類を開発する場合、パッケージ Framework のマネージ プロジェクトのクラスはの必要なインターフェイスを実装し、その実装を継承できます。 詳細については、次を参照してください。[パッケージの管理フレームワークを使用して、プロジェクトの種類 (c#) を実装する](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)です。  
  
-   C++ 開発者向けの HierUtil ライブラリのクラスには、同様の方法で動作します。 詳細については、次を参照してください。[ビルドに存在しません: プロジェクトの種類 (C++) を実装する HierUtil7 プロジェクト クラスを使用して](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)します。  
  
-   プロジェクトの種類には、.exe または .dll アセンブリにビルドを一般的なソース コード ファイル以外のデータをサポートできます。 たとえば、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]データベース プロジェクトがディスクに格納されているスクリプトとクエリのファイルへの参照を含めるし、するコマンドを追加**ソリューション エクスプ ローラー**を実行するスクリプトと、プロジェクトは、データベースに対するクエリ実行動作をサポートしないビルドします。 詳細については、次を参照してください。[開始タグとプロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)します。  
  
-   プロジェクトの種類は、すべてのファイルを使用する必要はありません。 たとえば、プロジェクトの種類は、データベースにそのすべてのデータを格納できます。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトの種類のプロジェクトとプロジェクト アイテムのデータを保存する方法を完全に制御を提供します。 詳細については、次を参照してください。[プロジェクトの種類のデザイン決定](../../extensibility/internals/project-type-design-decisions.md)します。  
  
-   プロジェクトの種類を指定する必要があります、*プロジェクト ファクトリ*、これは、プロジェクトのインスタンスを作成するオブジェクトを入力するたびに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を開くか、そのプロジェクトの種類に基づいているプロジェクトを作成するように指示されます。 詳細については、次を参照してください。[を作成するプロジェクト インスタンスで使用するプロジェクト ファクトリ](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)します。  
  
-   プロジェクトの種類には、プロジェクトとプロジェクト項目用のテンプレートを指定する必要があります。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ユーザーは、新しいプロジェクトを作成して、新しい項目を既存のプロジェクトに追加する場合は、テンプレートを使用します。 詳細については、次を参照してください。[プロジェクトに追加するとプロジェクト項目テンプレート](../../extensibility/internals/adding-project-and-project-item-templates.md)します。  
  
-   プロジェクトの種類には、デバッグやリリースなど、複数の構成をサポートできます。 ユーザーは、指定したプロパティ ページを使用して、プロジェクトのさまざまな構成を変更できます。 詳細については、次を参照してください。[構成オプションを管理する](../../extensibility/internals/managing-configuration-options.md)です。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクトの種類を展開します。](../../extensibility/internals/deploying-project-types.md)
