---
title: プロジェクトのタイプの基本情報 |Microsoft Docs
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
ms.openlocfilehash: b7daf114bb31019a499bc17e287df923107ee1a1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891571"
---
# <a name="project-type-essentials"></a>プロジェクト タイプの基本情報
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] などの言語のいくつかのプロジェクトの種類が含まれている[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]または[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]します。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] また、独自のプロジェクトの種類を作成してできます。  
  
 カスタム コマンド、エディター、またはツール ウィンドウを追加する場合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、新しいプロジェクトの種類を作成することがなく行うことができます。 詳細については、次のトピックを参照してください。  
  
- [コマンド、メニュー、およびツール バー](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
- [エディターと言語サービスの拡張機能](../../extensibility/editor-and-language-service-extensions.md)  
  
- [ツール ウィンドウの拡張とカスタマイズ](../../extensibility/extending-and-customizing-tool-windows.md)  
  
  同様に、指定されたの動作をカスタマイズする[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]と[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]プロジェクトの種類、行うことができますプロジェクト サブタイプを使用して。 詳細については、次を参照してください。[プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)します。  
  
  新しいプロジェクトの種類以外の言語に基づくプロジェクトを作成する必要があります[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]と[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]次の 1 つ以上をサポートする場合。  
  
- ビルド  
  
- 配置  
  
- 複数の構成  
  
- ソース管理  
  
- デバッグ  
  
- ソリューション エクスプ ローラーでプロジェクト項目  
  
- **プロジェクトを開く**または**新しいプロジェクト** ダイアログ ボックス  
  
- プロジェクトの入れ子  
  
- プロジェクトの種類の機能に関する詳細については、次を参照してください。  
  
- プロジェクトの種類は、一連のインターフェイスを実装する vspackage オブジェクト[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]が必要です。 を使用する c# プロジェクトの種類を開発する場合、Managed Package Framework プロジェクトのクラスはするのに必要なインターフェイスを実装し、その実装を継承することができます。 詳細については、次を参照してください。 [Managed Package Framework を使用して、プロジェクトの種類 (c#) を実装する](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)します。  
  
- C++ の開発者にとっては、HierUtil ライブラリのクラスは、同様の方法で動作します。 詳細については、次を参照してください。[ビルド内にありません: プロジェクトの種類 (C++) を実装する HierUtil7 プロジェクト クラスを使用して](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)します。  
  
- プロジェクトの種類には、.exe または .dll アセンブリにビルドされる一般的なソース コード ファイル以外のデータをサポートできます。 たとえば、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]データベース プロジェクトがディスクに格納されているスクリプトとクエリのファイルへの参照を含めるし、コマンドを追加**ソリューション エクスプ ローラー**を実行するスクリプトと、データベースが、プロジェクトに対するクエリ実行をサポートしていません動作を構築します。 詳細については、次を参照してください。[とプロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)します。  
  
- プロジェクトの種類をすべてのファイルを使用する必要はありません。 たとえば、プロジェクトの種類では、データベースにそのすべてのデータを格納できます。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] プロジェクトの種類のプロジェクトとプロジェクト アイテムのデータを保存する方法を完全に制御を提供します。 詳細については、次を参照してください。[プロジェクトの種類の設計に関する決定事項](../../extensibility/internals/project-type-design-decisions.md)します。  
  
- プロジェクトの種類を指定する必要があります、*プロジェクト ファクトリ*、プロジェクトのインスタンスを作成するオブジェクトがあるたびに入力[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]開くか、そのプロジェクトの種類に基づくプロジェクトを作成するように指示されます。 詳細については、次を参照してください。[を作成するプロジェクト インスタンスで使用してプロジェクト ファクトリ](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)します。  
  
- プロジェクトの種類には、プロジェクトとプロジェクト項目のテンプレートを指定する必要があります。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ユーザーが新しいプロジェクトを作成して、新しい項目を既存のプロジェクトに追加するときに、テンプレートを使用します。 詳細については、次を参照してください。[プロジェクトに追加するとプロジェクト項目テンプレート](../../extensibility/internals/adding-project-and-project-item-templates.md)します。  
  
- プロジェクトの種類には、デバッグやリリースなど、複数の構成をサポートできます。 ユーザーは、指定したプロパティ ページを使用して、プロジェクトのさまざまな構成を変更できます。 詳細については、次を参照してください。[構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)します。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト タイプの配置](../../extensibility/internals/deploying-project-types.md)