---
title: "Visual Studio のマルチ ターゲットの概要 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
ms.assetid: b1702c33-0672-4ebc-b779-2b324d6ea880
caps.latest.revision: 36
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 1a1b6d341325477c39ea3cb1faee029f78069325
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-multi-targeting-overview"></a>Visual Studio のマルチ ターゲットの概要
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のこのバージョンでは、アプリケーションで必要とされる [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョンを指定できます。 したがって、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のこのバージョンを使用して、以前のバージョンで開始したプロジェクトの開発を続ける場合は、対象のフレームワークを変更する必要はありません。 異なるバージョンのフレームワークを対象とする複数のプロジェクトを含むソリューションを作成することもできます。 特定のフレームワークを対象にする機能は、指定したバージョンのフレームワークで利用できる機能のみをアプリケーションで使用することを保証するのに役立ちます。  
  
> [!TIP]
>  異なるプラットフォームに対応する複数のアプリケーションを対象にすることもできます。 詳細については、「[Multitargeting](../msbuild/msbuild-multitargeting-overview.md)」(マルチターゲット) を参照してください。  
  
## <a name="framework-targeting-features"></a>フレームワークの対象設定機能  
 フレームワークの対象設定機能には、次の特徴があります。  
  
-   旧バージョンの [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] を対象とするプロジェクトを開いたときに、[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] でそのプロジェクトを自動的にアップグレードするか、前のバージョンを対象とした状態を維持することができます。  
  
-   プロジェクトを作成するときに、対象とする [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョンを指定できます。  
  
-   既存のプロジェクトの対象となっている [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョンを変更できます。  
  
-   同じソリューション内にある複数のプロジェクトのそれぞれで、異なるバージョンの [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] を対象とすることができます。  
  
-   プロジェクトの対象となる [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョンを変更すると、[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] では、参照ファイルおよび構成ファイルに対して必要な変更が加えられます。  
  
 旧バージョンの [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] を対象とするプロジェクトで作業する場合は、Visual Studio は開発環境で次のような変更を動的に行います。  
  
-   **[新しいプロジェクト]**、**[新しい項目の追加]**、**[新しい参照の追加]**、**[サービス参照の追加]** の各ダイアログ ボックスの項目をフィルター処理して、対象のバージョンで使用できない選択肢を除外します。  
  
-   **ツールボックス**内のカスタム コントロールをフィルター処理し、対象のバージョンで使用できないコントロールを除外したり、複数のコントロールが使用可能である場合に最新のコントロールのみを表示したりします。  
  
-   IntelliSense をフィルター処理して、対象のバージョンで使用できない言語機能を除外します。  
  
-   **プロパティ** ウィンドウのプロパティをフィルター処理して、対象のバージョンで使用できないプロパティを除外します。  
  
-   メニュー オプションをフィルター処理して、対象のバージョンで使用できないオプションを除外します。  
  
-   ビルドを行う場合は、対象のバージョンに適したコンパイラのバージョンおよびコンパイラ オプションを使用します。  
  
> [!NOTE]
>  フレームワークの対象機能は、開発中のアプリケーションが正しく実行されることを保証するわけではありません。 対象のバージョンで実行できるかどうかを確認するために、アプリケーションをテストする必要があります。 .NET Framework 2.0 より前のバージョンのフレームワークを対象にすることはできません。  
  
## <a name="selecting-a-target-framework-version"></a>対象フレームワークのバージョンの選択  
 プロジェクトを作成するときに、**[新しいプロジェクト]** ダイアログ ボックスで、対象の [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョンを選択します。 この選択内容に基づいて、使用できるプロジェクト テンプレートの一覧が抽出されます。 既存のプロジェクトでは、プロジェクトのプロパティ ダイアログ ボックス内で、対象となる [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョンを変更できます。 詳細については、「[How to: Target a Version of the .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)」(方法: .NET Framework のバージョンをターゲットにする) を参照してください。  
  
> [!NOTE]
>  Visual Studio Express Edition では、**[新しいプロジェクト]** ダイアログ ボックスで対象のフレームワークを設定することはできません。  
  
## <a name="resolving-system-and-user-assembly-references"></a>システム参照およびユーザー アセンブリ参照の解決  
 .NET Framework の特定のバージョンを対象にするには、最初に適切なアセンブリ参照をインストールする必要があります。 .NET Framework Version 2.0、3.0、および 3.5 に対応するアセンブリ参照は、.NET Framework 3.5 SP1 に含まれています。これは、[Microsoft ダウンロード センターの Microsoft Visual Studio](http://go.microsoft.com/fwlink/?LinkId=227602) Web サイトからダウンロードできます。 .NET Framework 3.5 Client Profile、.NET Framework 4、.NET Framework 4 Client Profile および Silverlight に対応するアセンブリ参照も、[Visual Studio のダウンロード](http://go.microsoft.com/fwlink/?LinkId=179687) Web サイトから入手できます。  
  
> [!NOTE]
>  .NET Framework クライアント プロファイルは、限定されたセットのライブラリと機能を備えた .NET Framework のサブセットです。 クライアント プロファイルの詳細については、「[.NET Framework Client Profile](http://msdn.microsoft.com/Library/f0219919-1f02-4588-8704-327a62fd91f1)」を参照してください。  
  
 **[参照の追加]** ダイアログ ボックスでは、対象の [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョンに関係しないシステム アセンブリが無効にされます。その結果、それらのアセンブリをプロジェクトに誤って追加することはありません  (システム アセンブリとは、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] バージョンの一部である .dll ファイルのことです)。対象より新しいバージョンのフレームワークに属する参照は解決されず、そのような参照に依存するコントロールを追加することはできません。 このような参照を有効にするには、プロジェクトの対象である [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] を、その参照を含むバージョンに再設定します。  詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。  
  
 アセンブリ参照の詳細については、「[Resolving Assemblies at Design Time](../msbuild/resolving-assemblies-at-design-time.md)」(デザイン時のアセンブリの解決) を参照してください。  
  
## <a name="enabling-linq"></a>LINQ の有効化  
 .NET Framework Version 3.5 以降を対象にする場合は、System.Core の参照と System.Linq のプロジェクトレベル インポート (Visual Basic のみ) が自動的に追加されます。 LINQ 機能を使用する場合は、[Option Infer] もオンにする必要があります (Visual Basic のみ)。 対象をそれより前のバージョンの .NET Framework に変更すると、この参照とインポートは自動的に削除されます。 詳細については、「[How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)」(方法: LINQ プロジェクトを作成する) を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [マルチターゲット](../msbuild/msbuild-multitargeting-overview.md)   
 [ASP.NET Web プロジェクト用の .NET Framework Multi-Targeting](http://msdn.microsoft.com/Library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)   
 [プラットフォームの互換性とシステム要件](http://www.microsoft.com/visualstudio/eng/products/compatibility)
