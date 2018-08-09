---
title: 登録と Vspackage を登録解除 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c9abdf432664e57dd773649a88f97cf9b48675d7
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638174"
---
# <a name="register-and-unregister-vspackages"></a>登録して、Vspackage の登録解除
属性を使用して、VSPackage の登録が、  
  
## <a name="register-a-vspackage"></a>VSPackage を登録します。  
 マネージ Vspackage の登録を制御するのに属性を使用できます。 すべての登録情報が含まれている、 *.pkgdef*ファイル。 ファイル ベースの登録の詳細については、次を参照してください。 [CreatePkgDef ユーティリティ](../extensibility/internals/createpkgdef-utility.md)します。  
  
 次のコードでは、標準登録属性を使用して、VSPackage を登録する方法を示します。  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregister-an-extension"></a>拡張機能の登録を解除します。  
 多くの異なる Vspackage みる実験用インスタンスから削除する場合、実行して、**リセット**コマンド。 探して**Visual Studio の実験用インスタンスをリセット**コンピューターのスタート ページで、コマンドラインからこのコマンドを実行または。  
  
```cmd  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Visual Studio の開発インスタンスにインストールされている拡張機能をアンインストールする場合を参照してください。**ツール** > **拡張機能と更新**、拡張機能を見つけて、をクリックします。**アンインストール**します。  
  
 何らかの理由には、拡張機能のアンインストールでこれらのメソッドのどちらも成功すると、コマンドラインから、VSPackage アセンブリを次のように登録解除できます。  
  
```cmd  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>  
```  
  
<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>  
  
## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>カスタム登録属性を使用して、拡張機能の登録  
  
場合によっては、拡張機能の新しい登録属性を作成する必要があります。 新しいレジストリ キーを追加したり既存のキーに新しい値を追加する登録属性を使用することができます。 新しい属性が派生する必要があります<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>、それをオーバーライドする必要があり、<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A>と<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A>メソッド。  
  
### <a name="create-a-custom-attribute"></a>カスタム属性を作成します。  
  
次のコードでは、新しい登録属性を作成する方法を示します。  
  
```csharp  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
```  
  
 <xref:System.AttributeUsageAttribute>属性クラスで属性に関連する、かどうかと指定できます 2 回以上継承するかどうかをプログラム要素 (クラス、メソッドなど) を指定するために使用します。  
  
### <a name="create-a-registry-key"></a>レジストリ キーを作成します。  
  
次のコードでは、カスタム属性を作成、**カスタム**登録される VSPackage のキーの下のサブキー。  
  
```csharp  
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
  
### <a name="create-a-new-value-under-an-existing-registry-key"></a>既存のレジストリ キーの下の新しい値を作成します。  
  
カスタム値は、既存のキーを追加できます。 次のコードでは、VSPackage の登録キーを新しい値を追加する方法を示します。  
  
```csharp  
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
  
## <a name="see-also"></a>関連項目  
 [VSPackage](../extensibility/internals/vspackages.md)
