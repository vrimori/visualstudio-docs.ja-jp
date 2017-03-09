---
title: "インストールと配置のよく寄せられる質問 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "配置 [Visual Studio SDK]"
  - "LCID [Visual Studio SDK]"
  - "インストール [Visual Studio SDK]"
ms.assetid: 4ac62bf3-e335-4899-9074-89bcd004dc65
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# インストールと配置のよく寄せられる質問
ここではインストールと配置の [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] のユーザー コミュニティからの質問について説明します。  トピックではコミュニティから新しいコンテンツが更新されます。  
  
## 内容  
  
-   [Visual Studio のインストールの LCID をプログラムによって決まります](#DeterminingtheLCIDofaVisualStudioInstallationProgrammatically)  
  
##  <a name="DeterminingtheLCIDofaVisualStudioInstallationProgrammatically"></a> Visual Studio のインストールの LCID をプログラムによって決まります  
 **: Q**  方法をプログラムで [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のインストールの LCID を確認できますか。  
  
 **A:**  <xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale2.GetUILocale%2A> または <xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale.GetUILocale%2A> は現在使用中の [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の LCID を返します。  
  
## 参照  
 [製品のリリース](../misc/releasing-a-visual-studio-integration-product.md)