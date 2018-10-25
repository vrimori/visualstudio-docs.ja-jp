---
title: セキュリティおよびローカライズされたサテライト アセンブリ | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- key pairs for strong-named assemblies
- strong-named assemblies, security considerations
- satellite assemblies, localized
- code signing, assemblies
- security [Visual Studio], assemblies
- strong-named assemblies, localized
- assemblies [Visual Studio], security
- localization, satellite assemblies
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d817569a5f6709794b452fb5efe38d584669033f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218648"
---
# <a name="security-and-localized-satellite-assemblies"></a>セキュリティおよびローカライズされたサテライト アセンブリ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

メイン アセンブリで厳密な名前付けを使用している場合、サテライト アセンブリをメイン アセンブリと同じ秘密キーで署名する必要があります。 公開キーと秘密キーのペアがメイン アセンブリとサテライト アセンブリで一致しない場合、リソースは読み込まれません。 アセンブリへの署名の詳細については、「[方法 : 厳密な名前でアセンブリに署名する](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67)」を参照してください。  
  
 通常、組織の署名のグループまたは外部の署名機関には、秘密キーを使って署名させる必要があります。 これは、秘密キーの機密性によるもので、多くの場合、アクセスは数人のユーザーに制限されます。 開発時には遅延署名を使用することができます。 詳細については、「[アセンブリへの遅延署名](http://msdn.microsoft.com/library/9d300e17-5bf1-4360-97da-2aa55efd9070)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [アセンブリのセキュリティに関する考慮事項](http://msdn.microsoft.com/library/1b5439c1-f3d5-4529-bd69-01814703d067)   
 [セキュリティの基本概念](http://msdn.microsoft.com/library/3cfced4f-ea02-4e66-ae98-d69286363e98)   
 [.NET Framework ベースの国際対応アプリケーションの概要](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [アプリケーションのローカライズ](../ide/localizing-applications.md)   
 [アプリケーションのグローバライズとローカライズ](../ide/globalizing-and-localizing-applications.md)

