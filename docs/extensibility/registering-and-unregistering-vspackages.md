---
title: "登録して、Vspackage の登録を解除する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 312c06295492ac9bd1136ea7de9a0399f247c365
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="registering-and-unregistering-vspackages"></a>Vspackage の登録および登録解除しています
属性を使用して、VSPackage を登録するが、  
  
## <a name="registering-a-vspackage"></a>VSPackage を登録します。  
 属性を使用すると、マネージ Vspackage の登録を制御します。 すべての登録情報は、.pkgdef ファイルに含まれます。 ファイル ベースの登録の詳細については、次を参照してください。 [CreatePkgDef ユーティリティ](../extensibility/internals/createpkgdef-utility.md)です。  
  
 次のコードは、標準登録属性を使用して、VSPackage を登録する方法を示しています。  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>拡張機能の登録を解除します。  
 多数の異なる Vspackage で実験されて、実験用インスタンスから削除する場合、できるだけを行う、**リセット**コマンド。 探して**Visual Studio の実験用インスタンスをリセット**コンピューターのスタート ページで、コマンドラインからこのコマンドを実行または。  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Visual Studio の開発インスタンスにインストールされている拡張機能をアンインストールする場合を参照してください。**ツール/拡張機能と更新**、拡張機能を見つけて、クリック**アンインストール**です。  
  
 何らかの理由には、拡張機能のアンインストールでこれらのメソッドのどちらも成功すると、コマンドラインから、VSPackage アセンブリを次のように登録解除できます。  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>  
```  
  
<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>  
  
## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>拡張機能の登録をカスタム登録属性を使用してください。  
  
特定の状況では、拡張機能の新しい登録属性を作成する必要があります。 新しいレジストリ キーを追加したり既存のキーに新しい値を追加するには、登録属性を使用することができます。 新しい属性が派生する必要があります<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>、それをオーバーライドする必要があります、<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A>と<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A>メソッドです。  
  
### <a name="creating-a-custom-attribute"></a>カスタム属性を作成します。  
  
次のコードでは、新しい登録属性を作成する方法を示します。  
  
```csharp  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
```  
  
 <xref:System.AttributeUsageAttribute>属性クラスで、プログラム要素 (クラス、メソッドなど) を属性の関連する、かどうかと指定できますも複数回継承するかどうかを指定するために使用します。  
  
### <a name="creating-a-registry-key"></a>レジストリ キーを作成します。  
  
次のコードでは、カスタム属性を作成、**カスタム**登録される VSPackage のキーの下のサブキーです。  
  
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
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>既存のレジストリ キーの下で新しい値を作成します。  
  
カスタム値は、既存のキーを追加できます。 次のコードは、VSPackage の登録キーを新しい値を追加する方法を示しています。  
  
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
