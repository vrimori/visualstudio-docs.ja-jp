---
title: 異なるバージョンの Microsoft Office でソリューションを実行します。
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], multiple Office versions
- Office applications [Office development in Visual Studio], multiple Office versions
- Office development in Visual Studio, multiple Office versions
- Office solutions [Office development in Visual Studio]
- multiple Office versions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 66199dd8bd5462eff40a0b8fdbdbbe8cbbc13234
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843399"
---
# <a name="run-solutions-in-different-versions-of-microsoft-office"></a>異なるバージョンの Microsoft Office でソリューションを実行します。
    
## <a name="run-office-solutions-created-by-using-visual-studio-2010-and-above"></a>Visual Studio 2010 を使用して、上に作成された Office ソリューションを実行します。  
  
|プロジェクト テンプレートが対象とする Office のバージョン|プロジェクトの .NET Framework をターゲット<sup>1</sup>|ソリューションを実行できる Office のバージョン|エンドユーザーのコンピューターに必要なランタイム|  
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|  
|Office 2016 と [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office system<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office system<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Visual Studio 2010 Tools for Office Runtime|  
|2007 Microsoft Office system|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降<br /><br /> または<br /><br /> .NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office system|Visual Studio 2010 Tools for Office Runtime|  
  
 1. .NET Framework のバージョンを実行するソリューションのエンド ユーザー コンピューターで、プロジェクトのターゲットは必須です。 たとえば、プロジェクトが .NET Framework 3.5 を対象とする場合、.NET Framework 3.5 はエンドユーザーのコンピューターに必要です。 この例で、ソリューションは実行されない場合のみ、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]がエンドユーザーのコンピューターにインストールされています。  
  
 2. このシナリオでは、ソリューションが [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] の新機能を使用しない場合にのみ、エラーが発生することなく 2007 Microsoft Office system で実行されます。  
  
## <a name="run-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>Visual Studio 2010 以前の Visual Studio のバージョンを使用して作成された Office ソリューションを実行します。  
 Microsoft Office アプリケーションは、Visual Studio 2010 以前のバージョンの Visual Studio を使用して作成されたソリューションを実行できます。 これらのソリューションは、異なるバージョンの [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] を必要とする場合があります。 異なるバージョンの[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]並行して、同じコンピューターにインストールできます。  
  
 次の表は、Microsoft Office のバージョンが、Visual Studio の以前のバージョンを使用して作成されたソリューションを実行し、どのバージョンの[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]と .NET Framework が各ソリューションに必要です。  
  
|ソリューションの作成に使用される Visual Studio のエディション|プロジェクト テンプレートが対象とする Office のバージョン|ソリューションを実行できる Office のバージョン|エンドユーザーのコンピューターに必要なランタイム|エンドユーザーのコンピューターに必要な .NET Framework のバージョン|  
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|  
|Visual Studio 2008 Professional<br /><br /> または<br /><br /> Visual Studio Team System 2008|2007 Microsoft Office system|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] <sup>1</sup><br /><br /> 2007 Microsoft Office system|Visual Studio 2010 Tools for Office Runtime<sup>1</sup><br /><br /> または<br /><br /> Visual Studio Tools for the Microsoft Office System (Version 3.0 Runtime)|.NET Framework 3.5|  
|VSTO 2005 SE での Visual Studio 2005 の以下のエディションのいずれかの<sup>2</sup>インストールします。<br /><br /> -Visual Studio 2005 Tools for Office<br />-Visual Studio Team System 2005<br />-Visual Studio 2005 Professional|2007 Microsoft Office system|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (32 ビットのみ<sup>3</sup>)<br /><br /> 2007 Microsoft Office system|Visual Studio 2005 Tools for Office Second Edition Runtime|.NET Framework 2.0、.NET Framework 3.0、または .NET Framework 3.5|  
|次のいずれかのエディションの Visual Studio<br /><br /> -Visual Studio 2008 Professional<br />-Visual Studio Team System 2008<br />-Visual Studio 2005 Tools for Office (VSTO 2005 SE の有無<sup>2</sup>インストール)<br />-Visual Studio Team System 2005 (VSTO 2005 SE の有無<sup>2</sup>インストール)<br />-VSTO 2005 SE での visual Studio 2005 Professional<sup>2</sup>インストール|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (32 ビットのみ<sup>3</sup>)<br /><br /> 2007 Microsoft Office system<br /><br /> Microsoft Office 2003|Visual Studio 2005 Tools for Office Second Edition Runtime|.NET Framework 2.0、.NET Framework 3.0、または .NET Framework 3.5|  
  
 1. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]アプリケーションには、Visual Studio 2010 Tools for Office ランタイムが含まれます。 そのため、これらのアプリケーション常に使用して、Visual Studio Tools ではなく、Visual Studio 2010 Tools for Office ランタイム、Microsoft Office system の (version 3.0 Runtime) このシナリオでは。 2007 Microsoft Office system のアプリケーションでは、Visual Studio 2010 Tools for Office Runtime または Visual Studio Tools for the Microsoft Office system (Version 3.0 Runtime) を使用できます。  
  
 2. VSTO 2005 SE は、Microsoft Office 2003 および 2007 Microsoft Office system 用の VSTO アドイン プロジェクト テンプレートを提供する無料の Visual Studio アドオンです。 Visual Studio 2005 Professional、Visual Studio 2005 Tools for Office、または Visual Studio Team System 2005 のエディションと共にインストールできます。 詳細については、次を参照してください。 [for Office Second Edition の Visual Studio 2005 Tools](http://go.microsoft.com/fwlink/?LinkId=148446)します。  
  
 3. Visual Studio 2005 Tools for Office Second Edition Runtime を必要とする Office ソリューションは、[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] および [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] の 64 ビット バージョンと互換性がありません。 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] または [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] の 64 ビット エディションでこれらのソリューションを実行するには、プロジェクトを [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] または 2007 Microsoft Office system を対象とする Visual Studio 2008 プロジェクトにアップグレードする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [設計および Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)   
 [Visual Studio のツール for Office runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [方法: Visual Studio での Office プロジェクトを作成します。](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Visual Studio のツール for Office runtime のインストール シナリオ](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Office ソリューションを開発コンピューターを構成します。](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)  
