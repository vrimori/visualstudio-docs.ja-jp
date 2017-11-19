---
title: "異なるバージョンの Microsoft Office でソリューションを実行している |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], multiple Office versions
- Office applications [Office development in Visual Studio], multiple Office versions
- Office development in Visual Studio, multiple Office versions
- Office solutions [Office development in Visual Studio]
- multiple Office versions
ms.assetid: 414e7741-c07d-4900-9d10-68b821413b3f
caps.latest.revision: "61"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93e365d335f835196576ad9ed10216e904e81f93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="running-solutions-in-different-versions-of-microsoft-office"></a>異なるバージョンの Microsoft Office でのソリューションの実行
    
## <a name="running-office-solutions-created-by-using-visual-studio-2010-and-above"></a>Visual Studio 2010 以降を使用して作成された Office ソリューションの実行  
  
|プロジェクト テンプレートが対象とする Office のバージョン|プロジェクトの .NET Framework を対象に<sup>1</sup>|ソリューションを実行できる Office のバージョン|エンド ユーザーのコンピューターに必要なランタイム|  
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|  
|Office 2016 と [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office system<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office system<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Visual Studio 2010 Tools for Office Runtime|  
|2007 Microsoft Office system|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降<br /><br /> 、または<br /><br /> .NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office system|Visual Studio 2010 Tools for Office Runtime|  
  
 1. ソリューションを実行するエンド ユーザーのコンピューターには、プロジェクトが対象とする .NET Framework のバージョンが必要です。 たとえば、プロジェクトが .NET Framework 3.5 を対象としている場合、エンド ユーザーのコンピューターには .NET Framework 3.5 が必要です。 この例では、エンド ユーザーのコンピューターに [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] しかインストールされていない場合、ソリューションは実行されません。  
  
 2. このシナリオでは、ソリューションが [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] の新機能を使用しない場合にのみ、エラーが発生することなく 2007 Microsoft Office system で実行されます。  
  
## <a name="running-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>Visual Studio 2010 以前のバージョンの Visual Studio を使用して作成された Office ソリューションの実行  
 Microsoft Office アプリケーションは、Visual Studio 2010 以前のバージョンの Visual Studio を使用して作成されたソリューションを実行できます。 これらのソリューションは、異なるバージョンの [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] を必要とする場合があります。 異なるバージョンの [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] を同じコンピューターに同時にインストールできます。  
  
 次の表は、Microsoft Office のバージョンが、Visual Studio の以前のバージョンを使用して作成されたソリューションを実行し、どのバージョンの[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].NET Framework は各ソリューションに必要とします。  
  
|ソリューションの作成に使用される Visual Studio のエディション|プロジェクト テンプレートが対象とする Office のバージョン|ソリューションを実行できる Office のバージョン|エンド ユーザーのコンピューターに必要なランタイム|エンド ユーザーのコンピューターに必要な .NET Framework のバージョン|  
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|  
|Visual Studio 2008 Professional<br /><br /> または<br /><br /> Visual Studio Team System 2008|2007 Microsoft Office system|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]および[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] <sup>1</sup><br /><br /> 2007 Microsoft Office system|Visual Studio 2010 Tools for Office Runtime<sup>1</sup><br /><br /> または<br /><br /> Visual Studio Tools for the Microsoft Office System (Version 3.0 Runtime)|.NET Framework 3.5|  
|VSTO 2005 se の Visual Studio 2005 の以下のエディションのいずれかの<sup>2</sup>インストールします。<br /><br /> -Visual Studio 2005 Tools for Office<br />-Visual Studio Team System 2005<br />-Visual Studio 2005 Professional|2007 Microsoft Office system|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]および[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)](32 ビットのみ<sup>3</sup>)<br /><br /> 2007 Microsoft Office system|Visual Studio 2005 Tools for Office Second Edition Runtime|.NET Framework 2.0、.NET Framework 3.0、または .NET Framework 3.5|  
|次のいずれかのエディションの Visual Studio<br /><br /> -Visual Studio 2008 Professional<br />-Visual Studio Team System 2008<br />-Visual Studio 2005 Tools for Office (VSTO 2005 SE の有無<sup>2</sup>インストール)<br />-Visual Studio Team System 2005 (VSTO 2005 SE の有無<sup>2</sup>インストール)<br />-VSTO 2005 se visual Studio 2005 Professional<sup>2</sup>インストール|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]および[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)](32 ビットのみ<sup>3</sup>)<br /><br /> 2007 Microsoft Office system<br /><br /> Microsoft Office 2003|Visual Studio 2005 Tools for Office Second Edition Runtime|.NET Framework 2.0、.NET Framework 3.0、または .NET Framework 3.5|  
  
 1. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] アプリケーションおよび [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] アプリケーションには、Visual Studio 2010 Tools for Office Runtime が含まれます。 そのため、このシナリオの場合、これらのアプリケーションでは、Visual Studio Tools for the Microsoft Office system (Version 3.0 Runtime) ではなく、Visual Studio 2010 Tools for Office Runtime を常に使用します。 2007 Microsoft Office system のアプリケーションでは、Visual Studio 2010 Tools for Office Runtime または Visual Studio Tools for the Microsoft Office system (Version 3.0 Runtime) を使用できます。  
  
 2. VSTO 2005 SE は、Microsoft Office 2003 および 2007 Microsoft Office system 用の VSTO アドイン プロジェクト テンプレートを提供する無料の Visual Studio アドオンです。 Visual Studio 2005 Professional、Visual Studio 2005 Tools for Office、または Visual Studio Team System 2005 のエディションと共にインストールできます。 詳細については、次を参照してください。 [Office Second Edition 用の Visual Studio 2005 Tools](http://go.microsoft.com/fwlink/?LinkId=148446)です。  
  
 3. Visual Studio 2005 Tools for Office Second Edition Runtime を必要とする Office ソリューションは、[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] および [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] の 64 ビット バージョンと互換性がありません。 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] または [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] の 64 ビット エディションでこれらのソリューションを実行するには、プロジェクトを [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] または 2007 Microsoft Office system を対象とする Visual Studio 2008 プロジェクトにアップグレードする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [設計と、Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)   
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Visual Studio Tools for Office Runtime Installation Scenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Office ソリューションを開発できるようにコンピューターを構成する](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)  
  
  