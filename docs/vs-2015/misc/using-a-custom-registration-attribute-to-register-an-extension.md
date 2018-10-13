---
title: カスタム登録属性を使用して、拡張機能を登録する |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
manager: douge
ms.openlocfilehash: 251c31efcbb8a72efac51f246e644a30a79ed999
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279839"
---
# <a name="using-a-custom-registration-attribute-to-register-an-extension"></a>カスタム登録属性を使用した拡張機能の登録
場合によっては、拡張機能の新しい登録属性を作成する必要があります。 新しいレジストリ キーを追加したり既存のキーに新しい値を追加する登録属性を使用することができます。 新しい属性が派生する必要があります<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>、それをオーバーライドする必要があり、<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A>と<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A>メソッド。  
  
## <a name="creating-a-custom-attribute"></a>カスタム属性を作成します。  
 次のコードでは、新しい登録属性を作成する方法を示します。  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 <xref:System.AttributeUsageAttribute>属性クラスで属性に関連する、かどうかと指定できます 2 回以上継承するかどうかをプログラム要素 (クラス、メソッドなど) を指定するために使用します。  
  
### <a name="creating-a-registry-key"></a>レジストリ キーの作成  
 次のコードでは、カスタム属性を作成、**カスタム**登録される VSPackage のキーの下のサブキー。  
  
```  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>既存のレジストリ キーの下の新しい値を作成します。  
 カスタム値は、既存のキーを追加できます。 次のコードでは、VSPackage の登録キーを新しい値を追加する方法を示します。  
  
```  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
  
```