---
title: '[アセンブリ情報] ダイアログ ボックス | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8526dfbe970c43e1ab55534c13a1e6708b2b4693
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248028"
---
# <a name="assembly-information-dialog-box"></a>[アセンブリ情報] ダイアログ ボックス
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
**[アセンブリ情報]** ダイアログ ボックスは、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] グローバル アセンブリ属性の値を指定するために使用します。この値は、プロジェクトで自動的に作成される AssemblyInfo ファイルに格納されます。 **ソリューション エクスプローラー**では、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] の **[マイ プロジェクト]** ノードにこのファイルがあります (**[すべてのファイルを表示]** をクリックして表示します)。これは [!INCLUDE[csprcs](../../includes/csprcs-md.md)] の **[プロパティ]** にあります。 アセンブリ属性の詳細については、「[属性](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)」を参照してください。  
  
 このダイアログ ボックスを表示するには、**ソリューション エクスプローラー**でプロジェクト ノードを選択し、**[プロジェクト]** メニューの **[プロパティ]** をクリックします。 **プロジェクト デザイナー**が表示されたら、**[アプリケーション]** タブをクリックします。**[アプリケーション]** ページで、**[アセンブリ情報]** ボタンをクリックします。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **タイトル**  
 アセンブリ マニフェストのタイトルを指定します。 <xref:System.Reflection.AssemblyTitleAttribute> に相当します。  
  
 **説明**  
 アセンブリ マニフェストの説明を指定します (省略可能)。 <xref:System.Reflection.AssemblyDescriptionAttribute> に相当します。  
  
 **会社名**  
 アセンブリ マニフェストの会社名を指定します。 <xref:System.Reflection.AssemblyCompanyAttribute> に相当します。  
  
 **製品**  
 アセンブリ マニフェストの製品名を指定します。 <xref:System.Reflection.AssemblyProductAttribute> に相当します。  
  
 **著作権**  
 アセンブリ マニフェストの著作権情報を指定します。 <xref:System.Reflection.AssemblyCopyrightAttribute> に相当します。  
  
 **商標**  
 アセンブリ マニフェストの商標を指定します。 <xref:System.Reflection.AssemblyTrademarkAttribute> に相当します。  
  
 **アセンブリ バージョン**  
 アセンブリのバージョンを指定します。 <xref:System.Reflection.AssemblyVersionAttribute> に相当します。  
  
 **ファイルのバージョン**  
 Win32 ファイル バージョン リソースの特定のバージョン番号を使用するようコンパイラに指示します。 <xref:System.Reflection.AssemblyFileVersionAttribute> に相当します。  
  
 **GUID**  
 アセンブリを示す一意の GUID。 プロジェクトを作成すると、Visual Studio でアセンブリの GUID が生成されます。 <xref:System.Guid> に相当します。  
  
 **ニュートラル言語**  
 アセンブリがサポートするカルチャを指定します。 <xref:System.Resources.NeutralResourcesLanguageAttribute> に相当します。 既定値は **[(なし)]** です。  
  
 **アセンブリを COM 参照可能にする**  
 アセンブリの型を COM に使用できるようにするかどうかを指定します。 <xref:System.Runtime.InteropServices.ComVisibleAttribute> に相当します。  
  
## <a name="see-also"></a>関連項目  
 [[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)   
 [属性](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)



