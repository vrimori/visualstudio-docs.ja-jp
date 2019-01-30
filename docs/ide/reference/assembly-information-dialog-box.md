---
title: '[アセンブリ情報] ダイアログ ボックス'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e6214ec04dbf45e7d6b5a973babe4c7d95b571b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020088"
---
# <a name="assembly-information-dialog-box"></a>[アセンブリ情報] ダイアログ ボックス
**[アセンブリ情報]** ダイアログ ボックスは、[!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] グローバル アセンブリ属性の値を指定するために使用します。この値は、プロジェクトで自動的に作成される AssemblyInfo ファイルに格納されます。 **ソリューション エクスプローラー**では、[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] の **[マイ プロジェクト]** ノードにこのファイルがあります (**[すべてのファイルを表示]** をクリックして表示します)。これは [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] の **[プロパティ]** にあります。 アセンブリ属性の詳細については、「[属性](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)」を参照してください。

 このダイアログ ボックスを表示するには、**ソリューション エクスプローラー**でプロジェクト ノードを選択し、**[プロジェクト]** メニューの **[プロパティ]** をクリックします。 **プロジェクト デザイナー**が表示されたら、**[アプリケーション]** タブをクリックします。**[アプリケーション]** ページで、**[アセンブリ情報]** ボタンをクリックします。

## <a name="uielement-list"></a>UIElement の一覧
 **タイトル** アセンブリ マニフェストのタイトルを指定します。 <xref:System.Reflection.AssemblyTitleAttribute> に相当します。

 **説明** アセンブリ マニフェストの説明を指定します (省略可能)。 <xref:System.Reflection.AssemblyDescriptionAttribute> に相当します。

 **会社** アセンブリ マニフェストの会社名を指定します。 <xref:System.Reflection.AssemblyCompanyAttribute> に相当します。

 **製品** アセンブリ マニフェストの製品名を指定します。 <xref:System.Reflection.AssemblyProductAttribute> に相当します。

 **著作権** アセンブリ マニフェストの著作権情報を指定します。 <xref:System.Reflection.AssemblyCopyrightAttribute> に相当します。

 **商標** アセンブリ マニフェストの商標を指定します。 <xref:System.Reflection.AssemblyTrademarkAttribute> に相当します。

 **アセンブリ バージョン** アセンブリのバージョンを指定します。 <xref:System.Reflection.AssemblyVersionAttribute> に相当します。

 **ファイル バージョン** Win32 ファイル バージョン リソースの特定のバージョン番号を使用するようコンパイラに指示します。 <xref:System.Reflection.AssemblyFileVersionAttribute> に相当します。

 **GUID** アセンブリを示す一意の GUID。 プロジェクトを作成すると、Visual Studio でアセンブリの GUID が生成されます。 <xref:System.Guid> に相当します。

 **ニュートラル言語** アセンブリがサポートするカルチャを指定します。 <xref:System.Resources.NeutralResourcesLanguageAttribute> に相当します。 既定値は **[(なし)]** です。

 **アセンブリを COM 参照可能にする** アセンブリの型を COM に使用できるようにするかどうかを指定します。 <xref:System.Runtime.InteropServices.ComVisibleAttribute> に相当します。

## <a name="see-also"></a>「

- [[アプリケーション] ページ (プロジェクト デザイナー)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [属性](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)