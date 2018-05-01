---
title: '方法 : プロジェクトを構成して対象プラットフォームを設定する | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc85686b9b60692a625e3e09403e0e7b571f2b2f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-configure-projects-to-target-platforms"></a>方法 : プロジェクトを構成して対象プラットフォームを設定する
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] では、64 ビット プラットフォームを含む、さまざまなプラットフォーム向けにアプリケーションを設定できます。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] での 64 ビット プラットフォームのサポートについて詳しくは、「[64 ビット アプリケーション](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)」を参照してください。  
  
## <a name="target-platforms-with-the-configuration-manager"></a>構成マネージャーを使用して対象プラットフォームを指定する  
 **構成マネージャー**を使うと、プロジェクトの対象となる新しいプラットフォームをすばやく追加できます。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] に用意されているプラットフォームのいずれかを選択すると、プロジェクトのプロパティは、選択したプラットフォーム向けにプロジェクトをビルドするように変更されます。  
  
#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>64 ビット プラットフォームを対象とするようにプロジェクトを構成するには  
  
1.  メニュー バーで **[ビルド]** > **[構成マネージャー]** の順に選択します。  
  
2.  **[アクティブ ソリューション プラットフォーム]** ボックスの一覧で、ソリューションの対象となる 64 ビット プラットフォームを選び、**[閉じる]** を選びます。  
  
    1.  必要なプラットフォームが表示されない場合は、**[アクティブ ソリューション プラットフォーム]** ボックスの一覧の **[新規作成]** を選びます。  
  
         **[新しいソリューション プラットフォーム]** ダイアログ ボックスが表示されます。  
  
    2.  **[新しいプラットフォームを入力または選択してください]** ボックスの一覧で、**[x64]** を選びます。  
  
        > [!NOTE]
        >  構成に新しい名前を指定する場合は、**[プロジェクト デザイナー]** で適切なプラットフォームを対象にするよう設定の変更が必要になることがあります。  
  
    3.  現在のプラットフォーム構成から設定をコピーする場合は、構成を選んでから **[OK]** を選びます。  
  
 64 ビット プラットフォームを対象とするすべてのプロジェクトのプロパティが更新され、プロジェクトの次のビルドは 64 ビット プラットフォーム用に最適化されます。  
  
## <a name="target-platforms-in-the-project-designer"></a>プロジェクト デザイナーで対象プラットフォームを指定する  
 **プロジェクト デザイナー**にも、さまざまなプラットフォームをプロジェクトの対象にする方法が用意されています。 **[新しいソリューション プラットフォーム]** ダイアログ ボックスの一覧にあるプラットフォームのいずれかを選んでも、ソリューションで機能しない場合は、カスタム構成名を作成し、**プロジェクト デザイナー**で設定を変更して、適切なプラットフォームを対象にすることができます。  
  
 このタスクの実行方法は、使用するプログラミング言語によって異なります。 詳細については、次のリンクを参照してください。  
  
-   [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] プロジェクトについては、「[/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform)」をご覧ください。  
  
-   [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] プロジェクトについては、「[[ビルド] ページ (プロジェクト デザイナー) (C#)](../ide/reference/build-page-project-designer-csharp.md)」を参照してください。  
  
-   [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] プロジェクトについては、「[/clr (Common Language Runtime compilation)](/cpp/build/reference/clr-common-language-runtime-compilation)」(/clr (共通言語ランタイムのコンパイル)) を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [ビルド プラットフォームについて](../ide/understanding-build-platforms.md)   
 [-platform (C# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)   
 [64 ビット アプリケーション](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Visual Studio IDE の 64 ビット サポート](../ide/visual-studio-ide-64-bit-support.md)