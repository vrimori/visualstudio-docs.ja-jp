---
title: "セキュリティおよびローカライズされたサテライト アセンブリ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
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
caps.latest.revision: 8
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 2bac6b9d00c52e782cf2993ce70c3bd3466aba55
ms.contentlocale: ja-jp
ms.lasthandoff: 05/30/2017

---
# セキュリティおよびローカライズされたサテライト アセンブリ
<a id="security-and-localized-satellite-assemblies" class="xliff"></a>
メイン アセンブリで厳密な名前付けを使用している場合、サテライト アセンブリをメイン アセンブリと同じ秘密キーで署名する必要があります。 公開キーと秘密キーのペアがメイン アセンブリとサテライト アセンブリで一致しない場合、リソースは読み込まれません。 アセンブリへの署名の詳細については、「[方法 : 厳密な名前でアセンブリに署名する](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)」を参照してください。  
  
 通常、組織の署名のグループまたは外部の署名機関には、秘密キーを使って署名させる必要があります。 これは、秘密キーの機密性によるもので、多くの場合、アクセスは数人のユーザーに制限されます。 開発時には遅延署名を使用することができます。 詳細については、「[アセンブリへの遅延署名](/dotnet/framework/app-domains/delay-sign-assembly)」を参照してください。  
  
## 関連項目
<a id="see-also" class="xliff"></a>  
 [アセンブリのセキュリティに関する考慮事項](/dotnet/framework/app-domains/assembly-security-considerations)   
 [セキュリティの基本概念](/dotnet/standard/security/key-security-concepts)   
 [.NET Framework ベースの国際対応アプリケーションの概要](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [アプリケーションのローカライズ](../ide/localizing-applications.md)   
 [アプリケーションのグローバライズとローカライズ](../ide/globalizing-and-localizing-applications.md)
