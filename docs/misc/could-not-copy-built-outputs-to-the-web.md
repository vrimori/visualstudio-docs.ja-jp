---
title: "ビルド出力を Web にコピーできません。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cantcopyoutputstoweb"
ms.assetid: 59cf714b-cf7d-4df9-81ae-d3254969d5bc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# ビルド出力を Web にコピーできません。
プロジェクト システムが、1 つ以上のビルド出力ファイル \(ビルドされた DLL、PDB、サテライト アセンブリなど\) を Web サーバーにコピーできませんでした。  
  
 このエラーは、1 つ以上のビルド出力ファイルが Web サーバーにコピーされなかったことを示しています。  
  
 このエラーは一般に、サーバー上でビルドの出力ファイルがロックされているか読み取り専用になっている場合に発生します。 サーバー上でファイルがロックされている場合は、現在サーバー上にあるアセンブリ、サテライト、またはデバッグ シンボルを [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ランタイムが適切にコピーできなかったことを示しています。  
  
 また、サーバーのディスク容量が不足しているか、ネットワークの問題によって [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がファイルを Web にアップロードできない可能性もあります。  
  
### このエラーを解決するには  
  
1.  ディスク容量を確認します。  
  
2.  ファイルがロックされている場合は、Web サーバーを再起動して、影響を受けるファイルに対する [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] のロックを解除します。  
  
## 参照  
 [PDB Files](http://msdn.microsoft.com/ja-jp/1761c84e-8c2c-4632-9649-b5f99964ed3f)