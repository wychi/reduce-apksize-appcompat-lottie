Apk Size Reduction - take appcompat / lottie as example
-------------------------------------------------------

Download size in KB

<table>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<tbody>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>ApkSize</p></td>
<td align="left"><p>dex</p></td>
<td align="left"><p>resources.arsc</p></td>
<td align="left"><p>res</p></td>
</tr>
<tr class="even">
<td align="left"><p>empty app</p></td>
<td align="left"><p>64.3</p></td>
<td align="left"><p>0.35</p></td>
<td align="left"><p>0.53</p></td>
<td align="left"><p>62.3</p></td>
</tr>
<tr class="odd">
<td align="left"><p>import AppCompat</p></td>
<td align="left"><p>435.7</p></td>
<td align="left"><p>167.8</p></td>
<td align="left"><p>49.7</p></td>
<td align="left"><p>222.8</p></td>
</tr>
<tr class="even">
<td align="left"><p>dummy_layout</p></td>
<td align="left"><p>228.3</p></td>
<td align="left"><p>0.65</p></td>
<td align="left"><p>48.9</p></td>
<td align="left"><p>198.6</p></td>
</tr>
<tr class="odd">
<td align="left"><p>aapt - remove res</p></td>
<td align="left"><p>113.4</p></td>
<td align="left"><p>0.65</p></td>
<td align="left"><p>48.9</p></td>
<td align="left"><p>63</p></td>
</tr>
<tr class="even">
<td align="left"><p>import lottie</p></td>
<td align="left"><p>200.8</p></td>
<td align="left"><p>84.1</p></td>
<td align="left"><p>49.1</p></td>
<td align="left"><p>63.2</p></td>
</tr>
<tr class="odd">
<td align="left"><p>resguard</p></td>
<td align="left"><p>196.5</p></td>
<td align="left"><p>84.1</p></td>
<td align="left"><p>40.9</p></td>
<td align="left"><p>63.2</p></td>
</tr>
<tr class="even">
<td align="left"><p>resguard[mod]</p></td>
<td align="left"><p>189.7</p></td>
<td align="left"><p>84.1</p></td>
<td align="left"><p>37.3</p></td>
<td align="left"><p>63.2</p></td>
</tr>
<tr class="odd">
<td align="left"><p>remove string</p></td>
<td align="left"><p>173.2</p></td>
<td align="left"><p>84.1</p></td>
<td align="left"><p>18.4</p></td>
<td align="left"><p>63.2</p></td>
</tr>
<tr class="even">
<td align="left"><p>Remove AppCompat Styles</p></td>
<td align="left"><p>149.2</p></td>
<td align="left"><p>73.5</p></td>
<td align="left"><p>5.7</p></td>
<td align="left"><p>62.4</p></td>
</tr>
<tr class="even">
<td align="left"><p>Remove XML entity</p></td>
<td align="left"><p>144.9</p></td>
<td align="left"><p>72.5</p></td>
<td align="left"><p>2.2</p></td>
<td align="left"><p>62.4</p></td>
</tr>
</tbody>
</table>

Empty App
---------

proguardFiles

1.  proguard-android-optimize.txt
2.  appt-rules.txt

![Screenshot from 2017-03-24 11:10:21.png](images/image18.png)

aapt\_rules.txt

![Screenshot from 2017-03-24 11:10:32.png](images/image09.png)

mapping.txt

![](images/image14.png)

### import AppComapt-v7

![](images/image05.png)

![](images/image10.png)

![](images/image06.png)

mapping.txt

![](images/image01.png)

### dummy\_layout

![](images/image08.png)

aapt\_rules.txt

![Screenshot from 2017-03-24 11:10:32.png](images/image09.png)

mapping.txt

![](images/image14.png)

### aapt - remove res

![](images/image13.png)

### import lottie

### ![](images/image02.png)

![](images/image12.png)

### ![](images/image00.png)

### resguard

![](images/image03.png)

### resguard [mod] - clean entity

![](images/image07.png)

[http://www.jianshu.com/p/60ce4bf20f72](https://www.google.com/url?q=http://www.jianshu.com/p/60ce4bf20f72&sa=D&ust=1490606924786000&usg=AFQjCNHEeuDZ4EaObUcehRFZd3NTzJRcyQ)

[http://blog.csdn.net/luoshengyang/article/details/8744683](https://www.google.com/url?q=http://blog.csdn.net/luoshengyang/article/details/8744683&sa=D&ust=1490606924787000&usg=AFQjCNEzm0BfgXgBZfTQLZZeAFGixTORPA)

com.tencent.mm.androlib.ApkDecoder\#decode

### Remove Strings

![](images/image17.png)

### Remove AppCompat - Style/Layout/Drawable reffed by values.xml

![](images/image11.png)

Reference
---------

gradle tasks

<table>
<col width="50%" />
<col width="50%" />
<tbody>
<tr class="odd">
<td align="left"><p>Gradle Tasks</p></td>
<td align="left"><p>Comments</p></td>
</tr>
<tr class="even">
<td align="left"><p>:app:generateReleaseResValues</p>
<p>:app:mergeReleaseResources</p>
<p>:app:processReleaseManifest</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>doFirst</p>
<p>replace files (layout/ …)</p>
<p>modify values.xml to remove styles</p></td>
</tr>
<tr class="even">
<td align="left"><p>:app:processReleaseResources</p>
<p></p>
<p></p>
<p></p></td>
<td align="left"><p>intermediates: (most of intermediates files are created at this point)</p>
<p></p>
<p>output:</p>
<p>aapt_rules.txt</p>
<p>resources-release.ap_</p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>doLast</p>
<p></p>
<p>remove PNGs from resources-release.ap_</p></td>
</tr>
<tr class="even">
<td align="left"><p>:app:transformClassesWithDexForRelease</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>:app:transformClassesWithShrinkResForRelease</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>:app:packageRelease</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>:app:assembleRelease</p></td>
<td align="left"><p>output: app-release.apk</p></td>
</tr>
<tr class="even">
<td align="left"><p>:app:resguardRelease</p></td>
<td align="left"><p>output: AndResGuard_app-release/app-release_signed_aligned.apk</p>
<p></p>
<p>rename res/*</p>
<p>remove entity R.drawable.XXX</p></td>
</tr>
</tbody>
</table>

Findings

styles -- ref --\> layout -- affect --\>  proguard (aapt\_rules.txt)

                   --\> drawable -- affect --\>  shrink resource

AppCompat

<table>
<col width="100%" />
<tbody>
<tr class="odd">
<td align="left"><p>values.xml</p>
<p></p>
<p><img src="images/image04.png" alt="Screenshot from 2017-03-23 11:50:07.png" /></p>
<p></p>
<p><img src="images/image15.png" alt="Screenshot from 2017-03-23 11:48:19.png" /></p></td>
</tr>
</tbody>
</table>

NOT WORKING (in this case)

<table>
<col width="100%" />
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://www.google.com/url?q=https://developer.android.com/studio/build/shrink-code.html%23keep-resources&amp;sa=D&amp;ust=1490606924821000&amp;usg=AFQjCNHAX_bOKREfOoj9VlGbinFsTIiIew">https://developer.android.com/studio/build/shrink-code.html#keep-resources</a></p>
<p></p>
<p>res/raw/keep.xml</p>
<p></p>
<p>&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;</p>
<p>&lt;resources xmlns:tools=&quot;http://schemas.android.com/tools&quot;</p>
<p>    tools:keep=&quot;@layout/l_used*_c,@layout/l_used_a,@layout/l_used_b*&quot;</p>
<p>    tools:discard=&quot;@layout/unused2&quot; /&gt;</p>
<p></p>
<p></p></td>
</tr>
</tbody>
</table>

Remove files directly will cause runtime exceptions

![](images/image16.png)

aapt commands

<table>
<col width="100%" />
<tbody>
<tr class="odd">
<td align="left"><p>Starting process 'command '/home/wychi/Android/Sdk/build-tools/25.0.2/aapt''. Working directory: /home/wychi/repository/AppCompatMin/app Command: /home/wychi/Android/Sdk/build-tools/25.0.2/aapt package -f --no-crunch -I /home/wychi/Android/Sdk/platforms/android-25/android.jar -M /home/wychi/repository/AppCompatMin/app/build/intermediates/manifests/full/release/AndroidManifest.xml -S /home/wychi/repository/AppCompatMin/app/build/intermediates/res/merged/release -m -J /home/wychi/repository/AppCompatMin/app/build/generated/source/r/release -F /home/wychi/repository/AppCompatMin/app/build/intermediates/res/resources-release.ap_ -G /home/wychi/repository/AppCompatMin/app/build/intermediates/proguard-rules/release/aapt_rules.txt --custom-package cms.appcompatmin -0 apk --output-text-symbols /home/wychi/repository/AppCompatMin/app/build/intermediates/symbols/release --no-version-vectors</p>
<p>Successfully started process 'command '/home/wychi/Android/Sdk/build-tools/25.0.2/aapt''</p>
<p></p></td>
</tr>
</tbody>
</table>

ref

Android gradle plugin

[http://google.github.io/android-gradle-dsl/javadoc/](https://www.google.com/url?q=http://google.github.io/android-gradle-dsl/javadoc/&sa=D&ust=1490606924832000&usg=AFQjCNF864zPEYsn835mzx8bnQOfHaZcEg)

[https://github.com/google/android-gradle-dsl](https://www.google.com/url?q=https://github.com/google/android-gradle-dsl&sa=D&ust=1490606924832000&usg=AFQjCNE5S8N52mGADK_qPQvsqwOIrQ2ZMA)

[https://android.googlesource.com/platform/tools/build/+/master/gradle/src/main/groovy/com/android/build/gradle/tasks/](https://www.google.com/url?q=https://android.googlesource.com/platform/tools/build/%2B/master/gradle/src/main/groovy/com/android/build/gradle/tasks/&sa=D&ust=1490606924833000&usg=AFQjCNGvPb7gNtHP6iTmtkbEMp5e1YrJcA)

git clone [https://android.googlesource.com/platform/tools/build](https://www.google.com/url?q=https://android.googlesource.com/platform/tools/build&sa=D&ust=1490606924834000&usg=AFQjCNFvbh-BfCMvYrJBk9KVYzQoAjeXqA)

[https://android.googlesource.com/platform/dalvik/+/a9ac3a9d1f8de71bcdc39d1f4827c04a952a0c29/dx/src/com/android/dx/command/dexer/Main.java?autodive=0](https://www.google.com/url?q=https://android.googlesource.com/platform/dalvik/%2B/a9ac3a9d1f8de71bcdc39d1f4827c04a952a0c29/dx/src/com/android/dx/command/dexer/Main.java?autodive%3D0&sa=D&ust=1490606924835000&usg=AFQjCNEyw3HYcE5qSzTIQKPXorbeQ1w6og)

Proguard

[https://www.guardsquare.com/en/proguard/manual/usage\#keepoptionmodifiers](https://www.google.com/url?q=https://www.guardsquare.com/en/proguard/manual/usage%23keepoptionmodifiers&sa=D&ust=1490606924836000&usg=AFQjCNGqsk269JATWtmTL19jOLKOdf3d7A)

<table>
<col width="100%" />
<tbody>
<tr class="odd">
<td align="left"><p>If you specify a class, without class members, ProGuard only preserves the class and its parameterless constructor as entry points. It may still remove, optimize, or obfuscate its other class members.</p>
<p>If you specify a method, ProGuard only preserves the method as an entry point. Its code may still be optimized and adapted.</p>
<p></p></td>
</tr>
<tr class="even">
<td align="left"><p>/home/wychi/repository/cmsecurity/build/intermediates/proguard-files/proguard-android-optimize.txt-2.3.0</p>
<p></p>
<p></p>
<p># Keep setters in Views so that animations can still work.</p>
<p>-keepclassmembers public class !android.support.v7.** extends android.view.View {</p>
<p>   void set*(***);</p>
<p>   *** get*();</p>
<p>}</p></td>
</tr>
</tbody>
</table>


