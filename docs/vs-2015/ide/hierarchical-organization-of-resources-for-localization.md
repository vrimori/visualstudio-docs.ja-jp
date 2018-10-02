---
title: ローカリゼーション用リソースの階層編成 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- resource files, localized
- localization [Visual Studio], resources
- fallback resources
- international applications [Visual Studio], storing resources
- satellite assemblies, resource hierarchies
- globalization [Visual Studio], resources
- satellite assemblies
- resources [Visual Studio], fallback system
- resource files, fallback processes
ms.assetid: dadf8f2c-f74c-44d7-bec0-a1e956d8d38d
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0e07d788f17469ab7a478f22dcf3aeffacfa9220
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546327"
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>ローカリゼーション用リソースの階層編成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio では、ローカライズされたリソース (各カルチャに対応した文字列や画像などのデータ) は、UI カルチャの設定に従って個別のファイルに保存され、読み込まれます。 ローカライズされたリソースの読み込みの仕組みを理解するには、リソースが階層状に整理されていると考えるとわかりやすくなります。  
  
## <a name="kinds-of-resources-in-the-hierarchy"></a>階層内のリソースの種類  
  
-   階層の最上部には、既定のカルチャ (英語 ("en") など) のフォールバック リソースが配置されています。 これは独自のファイルを持たない唯一のリソースであり、メイン アセンブリに格納されています。  
  
-   フォールバック リソースの下には、ニュートラル カルチャのリソースがあります。 ニュートラル カルチャは、言語に関連付けられ、国や地域には関連付けられません。 たとえば、フランス語 ("fr") はニュートラル カルチャです  (フォールバック リソースもニュートラル カルチャのリソースですが、特別なものであることに注意してください)。  
  
-   これらの下に、具体的なカルチャのリソースがあります。 具体的なカルチャは、言語および国/地域に関連付けられます。 たとえば、カナダ系フランス語 ("fr-CA") は、具体的なカルチャです。  
  
 アプリケーションがローカライズされたリソース (文字列など) を読み込もうとして見つけられなかった場合、要求されたリソースを含むリソース ファイルが見つかるまで上の階層へと移動します。  
  
 リソースを保存する最も良い方法は、できる限り汎用化することです。 つまり、可能であれば、具体的なカルチャではなくニュートラル カルチャのリソース ファイル内にローカライズされた文字列や画像を保存するということです。 たとえば、ベルギー系フランス語 ("fr-BE") カルチャのリソースがあり、そのすぐ上のリソースが英語のフォールバック リソースであるシステムのアプリケーションがあるとします。このアプリケーションを、別のユーザーがカナダ系フランス語のカルチャで構成されたシステムで開くと、問題が発生する可能性があります。 システムは "fr-CA" のサテライト アセンブリを検索しますが見つからないため、フランス語のリソースではなく、フォールバック リソース (この場合は英語) が含まれるメイン アセンブリを読み込みます。 次の図に、こうした好ましくないシナリオを示します。  
  
 ![特定のリソースのみ](../ide/media/vbspecificresourcesonly.gif "vbSpecificResourcesOnly")  
  
 推奨方法に従って "fr" カルチャのニュートラル リソース ファイル内にできる限り多くのリソースを配置した場合、カナダ系フランス語ユーザーに "fr-BE" カルチャ用のリソースは表示されませんが、文字列はフランス語で表示されます。 次の状況は、この推奨シナリオを示しています。  
  
 ![NeutralSpecificResources のグラフィック](../ide/media/vbneutralspecificresources.gif "vbNeutralSpecificResources")  
  
## <a name="see-also"></a>関連項目  
 [ローカリゼーションのニュートラル リソース言語](../ide/neutral-resources-languages-for-localization.md)   
 [セキュリティおよびローカライズされたサテライト アセンブリ](../ide/security-and-localized-satellite-assemblies.md)   
 [アプリケーションのローカライズ](../ide/localizing-applications.md)   
 [アプリケーションのグローバライズとローカライズ](../ide/globalizing-and-localizing-applications.md)   
 [方法: Windows フォームのグローバリゼーション用のカルチャおよび UI カルチャを設定する](http://msdn.microsoft.com/en-us/694e049f-0b91-474a-9789-d35124f248f0)   
 [方法: ASP.NET Web ページのグローバリゼーション用のカルチャおよび UI カルチャを設定する](http://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0)

