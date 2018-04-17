---
title: プロジェクトの種類の Essentials |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aff6cc669d7df46acaa2cbcb129a6b13b7261d9b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="project-type-essentials"></a>プロジェクトの種類の基本事項
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] などの言語のいくつかのプロジェクトの種類が含まれる[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]または[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]です。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 独自のプロジェクトの種類を作成することもできます。  
  
 カスタムのコマンド、エディター、またはツール ウィンドウを追加するだけの場合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、新しいプロジェクトの種類を作成しなくても実行できます。 詳細については、次のトピックを参照してください。  
  
-   [コマンド、メニュー、およびツール バー](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
-   [エディターと言語サービスの拡張機能](../../extensibility/editor-and-language-service-extensions.md)  
  
-   [ツール ウィンドウの拡張とカスタマイズ](../../extensibility/extending-and-customizing-tool-windows.md)  
  
 同様に、指定された動作をカスタマイズするかどうか[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]と[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]プロジェクト タイプで行うことができますプロジェクトのサブタイプを使用しています。 詳細については、次を参照してください。[プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)です。  
  
 新しいプロジェクトの種類以外の言語に基づくプロジェクトを作成する必要があります[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]と[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]次の 1 つ以上をサポートする場合。  
  
-   ビルド  
  
-   配置  
  
-   複数の構成  
  
-   ソース管理  
  
-   デバッグ  
  
-   ソリューション エクスプ ローラーでプロジェクト項目  
  
-   **プロジェクトを開く**または**新しいプロジェクト** ダイアログ ボックス  
  
-   プロジェクトの入れ子  
  
-   プロジェクトの種類の機能に関する詳細については、次を参照してください。  
  
-   プロジェクトの種類は、一連のインターフェイスを実装する VSPackage オブジェクト[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]が必要です。 を使用する C# の場合、プロジェクトの種類を開発する場合、Managed Package Framework プロジェクト クラスはの必要なインターフェイスを実装して、その実装を継承できます。 詳細については、次を参照してください。 [Managed Package Framework を使用して、プロジェクトの種類 (c#) を実装する](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)です。  
  
-   C++ 開発者 HierUtil ライブラリのクラスには、同様の方法で機能します。 詳細については、次を参照してください。[ビルド内にありません: プロジェクトの種類 (C++) を実装する HierUtil7 プロジェクト クラスを使用して](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)です。  
  
-   プロジェクトの種類は、.exe または .dll アセンブリにビルドの典型的なソース コード ファイル以外のデータをサポートできます。 たとえば、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]データベース プロジェクトがディスクに格納されているスクリプトやクエリのファイルへの参照を含めるし、するコマンドを追加**ソリューション エクスプ ローラー**を実行する、スクリプトと、データベースが、プロジェクトに対してクエリをサポートしません動作を構築します。 詳細については、次を参照してください。[開始タグとプロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)です。  
  
-   プロジェクトの種類をすべてのファイルを使用する必要はありません。 たとえば、プロジェクトの種類をデータベースにそのすべてのデータを格納する可能性があります。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] プロジェクトの種類のプロジェクトとプロジェクト アイテムのデータを保存する方法を完全に制御を提供します。 詳細については、次を参照してください。[プロジェクトの種類の設計に関する決定事項](../../extensibility/internals/project-type-design-decisions.md)です。  
  
-   プロジェクトの種類を指定する必要があります、*プロジェクト ファクトリ*、プロジェクトのインスタンスを作成するオブジェクトでは入力するたびに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]開くか、そのプロジェクトの種類に基づいているプロジェクトを作成するように指示されます。 詳細については、次を参照してください。[を作成するプロジェクト インスタンスで使用してプロジェクト ファクトリ](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)です。  
  
-   プロジェクトの種類は、プロジェクトとプロジェクト項目用のテンプレートを指定する必要があります。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ユーザーが新しいプロジェクトを作成し、新しい項目を既存のプロジェクトに追加すると、テンプレートを使用します。 詳細については、次を参照してください。[プロジェクトに追加するとプロジェクト項目テンプレート](../../extensibility/internals/adding-project-and-project-item-templates.md)です。  
  
-   プロジェクトの種類は、デバッグやリリースなどの複数の構成をサポートできます。 ユーザーは、指定したプロパティ ページを使用して、プロジェクトのさまざまな構成を変更できます。 詳細については、次を参照してください。[構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)です。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト タイプの配置](../../extensibility/internals/deploying-project-types.md)