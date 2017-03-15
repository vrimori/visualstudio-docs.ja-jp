---
title: "MSBuild エラー MSB3155 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.ProductNotFound"
helpviewer_keywords: 
  - "MSB3155"
ms.assetid: 59bf2293-ef13-4bb1-8f29-5d6966bbe313
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3155
**MSBuild エラー MSB3155: 項目 '\<パッケージ\>' が '\<パス\>' で見つかりませんでした。**  
  
 このエラーは、指定された <xref:Microsoft.Build.Tasks.Deployment.Bootstrapper.Product.ProductCode%2A> を使用するパッケージがブートストラップ キャッシュに見つからない場合に発生します。  
  
> [!NOTE]
>  Microsoft Data Access Components \(MDAC\) は、ブートストラップ パッケージには含まれなくなりました。  [Microsoft Windows Update](http://go.microsoft.com/fwlink/?LinkId=86676) の Web サイトからダウンロードできます。  
  
### このエラーを解決するには  
  
-   インストールするパッケージのリストから問題のパッケージを削除するか、そのパッケージをキャッシュに追加します。  また、マニフェストが妥当な XML タグを使用した正しい形式になっていることを確認します。  
  
## 参照  
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)   
 [\[必須コンポーネント\] ダイアログ ボックス](../Topic/Prerequisites%20Dialog%20Box.md)   
 [ブートストラップ パッケージの作成](../deployment/creating-bootstrapper-packages.md)