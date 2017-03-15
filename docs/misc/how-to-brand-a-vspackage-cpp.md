---
title: "方法: VSPackage をブランド化する (C++) | Microsoft Docs"
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
  - "[バージョン情報] ダイアログ ボックス"
  - "VSPackage、スプラッシュ スクリーン"
  - "VSPackage、ブランド化"
ms.assetid: a1b9213f-8702-4716-8623-cd3705d531fa
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# 方法: VSPackage をブランド化する (C++)
\[出力\] ダイアログ ボックス ENT0ENTスプラッシュ スクリーンに表示するにはVSPackage は <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> のインターフェイスを実装する必要があります。  これを行うには [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] に次の情報を指定します :  
  
-   名前  
  
-   シリアルまたはバージョン番号などID  
  
-   情報  
  
-   ロゴのアイコン  
  
 `IVsInstalledProductImpl` のクラスは情報のテンプレート パラメーターを受け取ります。  各テンプレート パラメーターは ID です。  最初の 3 つが文字列のリソース id を表し四分の一はアイコンのリソース id。  
  
## 使用例  
 VSPackage のクラスに次の宣言はクラスから [VSSDK のサンプル](../misc/vssdk-samples.md) あります。  
  
```  
class ATL_NO_VTABLE BasicPackage :   
  ...  
  public IVsInstalledProductImpl<  
    IDS_BASICPACKAGE_PRODUCT_NAME,  
    IDS_BASICPACKAGE_PRODUCT_IDENTIFIER,   
    IDS_BASICPACKAGE_PRODUCT_DETAILS,   
    IDI_BASICPACKAGE_LOGO>  
```  
  
 VSPackage をテストするには[方法: バージョン情報とスプラッシュ スクリーンをテストする](../misc/how-to-test-the-help-about-and-splash-screens.md) を参照してください。  
  
## 参照  
 [VSPackage のブランド化](/visual-cpp/misc/vspackage-branding)