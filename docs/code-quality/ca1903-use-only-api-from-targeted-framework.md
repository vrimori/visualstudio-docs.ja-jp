---
title: "CA1903: 対象のフレームワークから API のみを使用します | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseOnlyAPIFromTargetedFramework"
  - "CA1903"
helpviewer_keywords: 
  - "CA1903"
  - "UseOnlyApiFromTargetedFramework"
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1903: 対象のフレームワークから API のみを使用します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseOnlyApiFromTargetedFramework|  
|CheckId|CA1903|  
|分類|Microsoft.Portability|  
|互換性に影響する変更点|あり \- 外部から参照できるメンバーまたは型のシグネチャに対して適用された場合。<br /><br /> なし \- メソッドの本体で適用された場合。|  
  
## 原因  
 メンバーまたは型が、プロジェクトの対象のフレームワークに含まれていない Service Pack で導入されたメンバーまたは型を使用しています。  
  
## 規則の説明  
 新しいメンバーと種類が、.NET Framework 2.0 Service Pack 1 および 2、.NET Framework 3.0 Service Pack 1 および 2、および .NET Framework 3.5 Service Pack 1 に含まれました。  メジャー バージョンの .NET Framework を対象にしたプロジェクトは、これらの新しい API に意図せず依存する可能性があります。  このような依存関係を回避するために、この規則は、既定でプロジェクトのターゲット フレームワークに含まれなかったすべての新しいメンバーと型の使用に適用されます。  
  
 **ターゲット フレームワークと Service Pack の依存関係**  
  
|||  
|-|-|  
|ターゲット フレームワーク|規則が適用されるメンバーが導入された Service Pack|  
|.NET Framework 2.0|.NET Framework 2.0 SP1、.NET Framework 2.0 SP2|  
|.NET Framework 3.0|.NET Framework 2.0 SP1、.NET Framework 2.0 SP2、.NET Framework 3.0 SP1、.NET Framework 3.0 SP2|  
|.NET Framework 3.5|.NET Framework 3.5 SP1|  
|.NET Framework 4|なし|  
  
 プロジェクトのターゲット フレームワークを変更するには、「[対象となる特定の .NET Framework バージョンの指定](../ide/targeting-a-specific-dotnet-framework-version.md)」を参照してください。  
  
## 違反の修正方法  
 Service Pack への依存関係を削除するには、新しいメンバーまたは型のすべての使用を削除します。  これが意図的な依存関係である場合は、警告を抑制するか、この規則を無効にします。  
  
## 警告を抑制する状況  
 指定した Service Pack への意図的な依存関係でない場合は、この規則による警告を抑制しないでください。  この場合、この Service Pack がインストールされていないシステムでは、アプリケーションを実行できないことがあります。  これが意図的な依存関係である場合は、警告を抑制するか、この規則を無効にします。  
  
## 使用例  
 次の例は、.NET 2.0 Service Pack 1 でのみ使用できる DateTimeOffset 型を使用するクラスを示しています。  この例では、\[プロジェクトのプロパティ\] の \[ターゲット フレームワーク\] ボックスの一覧で .NET Framework 2.0 を選択しておく必要があります。  
  
 [!code-cs[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]  
  
## 使用例  
 DateTimeOffset 型を DateTime 型の使用に置き換えて、前に説明した違反を修正する例を次に示します。  
  
 [!code-cs[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]  
  
## 参照  
 [移植性に関する警告](../code-quality/portability-warnings.md)   
 [対象となる特定の .NET Framework バージョンの指定](../ide/targeting-a-specific-dotnet-framework-version.md)