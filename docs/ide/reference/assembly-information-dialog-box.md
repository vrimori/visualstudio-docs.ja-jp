---
title: "[アセンブリ情報] ダイアログ ボックス | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 13
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
ms.openlocfilehash: 1a215cb25c14137f1ccc535833261a5bfc5f7a02
ms.lasthandoff: 02/22/2017

---
# <a name="assembly-information-dialog-box"></a>[アセンブリ情報] ダイアログ ボックス
**[アセンブリ情報]** ダイアログ ボックスは、[!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] グローバル アセンブリ属性の値を指定するために使用します。この値は、プロジェクトで自動的に作成される AssemblyInfo ファイルに格納されます。 **ソリューション エクスプローラー**では、[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] の **[マイ プロジェクト]** ノードにこのファイルがあります (**[すべてのファイルを表示]** をクリックして表示します)。これは [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] の **[プロパティ]** にあります。 アセンブリ属性の詳細については、「[属性](http://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)」を参照してください。  
  
 このダイアログ ボックスを表示するには、**ソリューション エクスプローラー**でプロジェクト ノードを選択し、**[プロジェクト]** メニューの **[プロパティ]** をクリックします。 **プロジェクト デザイナー**が表示されたら、**[アプリケーション]** タブをクリックします。 **[アプリケーション]** ページで、**[アセンブリ情報]** ボタンをクリックします。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **タイトル**  
 アセンブリ マニフェストのタイトルを指定します。 <xref:System.Reflection.AssemblyTitleAttribute> に対応します。  
  
 **説明**  
 アセンブリ マニフェストの説明を指定します (省略可能)。 <xref:System.Reflection.AssemblyDescriptionAttribute> に対応します。  
  
 **会社名**  
 アセンブリ マニフェストの会社名を指定します。 <xref:System.Reflection.AssemblyCompanyAttribute> に対応します。  
  
 **製品**  
 アセンブリ マニフェストの製品名を指定します。 <xref:System.Reflection.AssemblyProductAttribute> に対応します。  
  
 **著作権**  
 アセンブリ マニフェストの著作権情報を指定します。 <xref:System.Reflection.AssemblyCopyrightAttribute> に対応します。  
  
 **商標**  
 アセンブリ マニフェストの商標を指定します。 <xref:System.Reflection.AssemblyTrademarkAttribute> に対応します。  
  
 **アセンブリ バージョン**  
 アセンブリのバージョンを指定します。 <xref:System.Reflection.AssemblyVersionAttribute> に対応します。  
  
 **ファイルのバージョン**  
 Win32 ファイル バージョン リソースの特定のバージョン番号を使用するようコンパイラに指示します。 <xref:System.Reflection.AssemblyFileVersionAttribute> に対応します。  
  
 **GUID**  
 アセンブリを示す一意の GUID。 プロジェクトを作成すると、Visual Studio でアセンブリの GUID が生成されます。 <xref:System.Guid> に対応します。  
  
 **ニュートラル言語**  
 アセンブリがサポートするカルチャを指定します。 <xref:System.Resources.NeutralResourcesLanguageAttribute> に対応します。 既定値は **[(なし)]** です。  
  
 **アセンブリを COM 参照可能にする**  
 アセンブリの型を COM に使用できるようにするかどうかを指定します。 <xref:System.Runtime.InteropServices.ComVisibleAttribute> に対応します。  
  
## <a name="see-also"></a>関連項目  
 [[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)   
 [属性](http://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
