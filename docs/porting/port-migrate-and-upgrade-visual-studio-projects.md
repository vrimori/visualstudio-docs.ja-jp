---
title: "Visual Studio プロジェクトのポート、移行、アップグレード | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: ae6564f10ca561853444698665779bd1014d4afd
ms.openlocfilehash: 2915a9ceec638471ac29599992a7ccdff17cefb4

---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Visual Studio プロジェクトのポート、移行、アップグレード
Visual Studio の新しいバージョンに移行する場合、前のバージョンで作成したソリューション、プロジェクト、ファイル、その他のアセットを最近のバージョンで実行する*前*に、それらを変更する必要があるかどうかを把握する必要があります。

 幅広く使用されている多くのアセットは、新しいバージョン Visual Studio 2017 RC でも、現在のバージョン Visual Studio 2015 と同様に動作します。 また、以前のバージョン Visual Studio 2013 および Visual Studio 2012 でも同じように動作します。

 たとえば、Visual Studio 2017 RC では、Visual Studio 2015 または Visual Studio 2013 で作成したプロジェクトを開いて変更を加え、Visual Studio 2017 RC で開きなおすことができます。変更内容は保持され、プロジェクトは前のバージョンと同じように動作します。 これは、Visual Studio 2012 で作成した多くのアセットにも当てはまります。  

 Visual Studio 2015 を Visual Studio 2013、Visual Studio 2012、または Visual Studio 2010 SP1 と共に使用する場合は、これらのバージョンのいずれでもプロジェクトとファイルを作成および変更できます。 いずれかのバージョンでサポートされていない機能を追加しない限り、バージョン間でプロジェクトとファイルを移行できます。 (バージョンごとの固有の機能については、[リリース ノート](https://www.visualstudio.com/vs/release-notes/)を参照してください。)



<!--HONumber=Feb17_HO4-->


