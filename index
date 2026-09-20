import React, { useState, useCallback, useEffect, useMemo, useRef } from 'react';
import { 
  ShoppingCart, CreditCard, Banknote, Smartphone, CheckCircle, 
  HeartPulse, Dog, Cat, Tractor, Plus, Minus, Trash2, ArrowLeft, 
  ChevronRight, Pill, UploadCloud, FileText, Search, X, 
  PhoneCall, Phone, ShieldCheck, MapPin, Loader2, Map,
  Info, HelpCircle, Mail, Clock, ChevronDown,
  Instagram, Facebook, Youtube, Linkedin, Play, Apple
} from 'lucide-react';

const inventoryData = {
  human: [
    { id: 'h1', subcategory: 'Pain Management', name: 'Paracetamol', desc: 'The most globally used non-opioid medicine for managing pain and reducing fever.', price: 45 },
    { id: 'h2', subcategory: 'Pain Management', name: 'Ibuprofen', desc: 'A standard NSAID used to alleviate pain, swelling, and chronic inflammation.', price: 55 },
    { id: 'h3', subcategory: 'Pain Management', name: 'Aspirin', desc: 'Used for minor pain and fever relief, and broadly utilized to prevent heart attacks.', price: 30 },
    { id: 'h4', subcategory: 'Palliative Care', name: 'Morphine', desc: 'The primary opioid narcotic used to treat severe, acute, or chronic pain.', price: 350 },
    { id: 'h5', subcategory: 'Anti-Infectives', name: 'Amoxicillin', desc: 'A highly vital, first-line penicillin antibiotic used to resolve common bacterial infections.', price: 120 },
    { id: 'h6', subcategory: 'Antibiotics', name: 'Ceftriaxone', desc: 'A powerful, broad-spectrum injectable cephalosporin antibiotic.', price: 200 },
    { id: 'h7', subcategory: 'Antibiotics', name: 'Ciprofloxacin', desc: 'A fluoroquinolone antibiotic used to manage severe urinary tract infections.', price: 140 },
    { id: 'h8', subcategory: 'Anti-Infectives', name: 'Metronidazole', desc: 'Core medication used against anaerobic bacterial infections and protozoal conditions.', price: 85 },
    { id: 'h9', subcategory: 'Antibiotics', name: 'Doxycycline', desc: 'Versatile tetracycline choice for respiratory infections and malaria prevention.', price: 110 },
    { id: 'h10', subcategory: 'Anti-Infectives', name: 'Aciclovir', desc: 'Primary antiviral medicine engineered to treat herpes simplex and shingles.', price: 210 },
    { id: 'h11', subcategory: 'Anti-Infectives', name: 'Albendazole', desc: 'Widely deployed antiparasitic dewormer utilized to treat systemic worm infections.', price: 40 },
    { id: 'h12', subcategory: 'Cardiovascular', name: 'Amlodipine', desc: 'Calcium channel blocker used daily to treat high blood pressure.', price: 90 },
    { id: 'h13', subcategory: 'Cardiovascular', name: 'Enalapril', desc: 'ACE inhibitor used to lower elevated blood pressure and manage heart failure.', price: 105 },
    { id: 'h14', subcategory: 'Cardiovascular', name: 'Atorvastatin', desc: 'Lipid-lowering statin used to decrease high cholesterol.', price: 180 },
    { id: 'h15', subcategory: 'Cardiovascular', name: 'Furosemide', desc: 'Crucial loop diuretic used to flush excess fluid caused by heart failure.', price: 65 },
    { id: 'h16', subcategory: 'Endocrine', name: 'Metformin', desc: 'First-line oral medicine used globally to safely manage type 2 diabetes.', price: 75 },
    { id: 'h17', subcategory: 'Endocrine', name: 'Insulin', desc: 'Life-saving injectable hormone required to control blood sugar levels.', price: 450 },
    { id: 'h18', subcategory: 'Endocrine', name: 'Levothyroxine', desc: 'Synthetic hormone prescribed to replace deficient thyroid levels.', price: 130 },
    { id: 'h19', subcategory: 'Neurological', name: 'Diazepam', desc: 'Benzodiazepine used for continuous seizures, severe anxiety, or alcohol withdrawal.', price: 115 },
    { id: 'h20', subcategory: 'Neurological', name: 'Carbamazepine', desc: 'Primary anticonvulsant used to prevent epileptic seizures.', price: 145 },
    { id: 'h21', subcategory: 'Mental Health', name: 'Amitriptyline', desc: 'Tricyclic agent for managing major depressive disorders and neuropathic pain.', price: 95 },
    { id: 'h22', subcategory: 'Respiratory', name: 'Salbutamol', desc: 'Rapid-acting bronchodilator rescue inhaler for acute asthma attacks.', price: 220 },
    { id: 'h23', subcategory: 'Allergy', name: 'Epinephrine', desc: 'Emergency injectable medication for severe allergic reactions (anaphylaxis).', price: 650 },
    { id: 'h24', subcategory: 'Allergy', name: 'Prednisolone', desc: 'Oral corticosteroid used to calm severe asthma or inflammatory flare-ups.', price: 80 },
    { id: 'h25', subcategory: 'Respiratory', name: 'Dexamethasone', desc: 'Potent anti-inflammatory steroid used in critical respiratory distress.', price: 90 },
    { id: 'h26', subcategory: 'Gastrointestinal', name: 'Omeprazole', desc: 'Standard PPI used to treat acid reflux, heartburn, and stomach ulcers.', price: 110 },
    { id: 'h27', subcategory: 'Rehydration', name: 'Oral Rehydration Salts', desc: 'Balanced powder blend to safely treat and prevent deadly dehydration.', price: 25 },
    { id: 'h28', subcategory: 'Emergency', name: 'Hydrocortisone', desc: 'Foundational steroid used for severe allergic crises.', price: 140 },
    { id: 'h29', subcategory: 'Emergency', name: 'Atropine', desc: 'Vital emergency drug given to reverse specific poisonings.', price: 85 },
    { id: 'h30', subcategory: 'Surgical', name: 'Heparin', desc: 'Rapid-acting injectable anticoagulant essential for preventing blood clots.', price: 320 }
  ],
  dog: [
    { id: 'd1', subcategory: 'Antiparasitics', name: 'Afoxolaner', desc: 'Oral preventative used to control and treat flea and tick infestations.', price: 850 },
    { id: 'd2', subcategory: 'Antiparasitics', name: 'Ivermectin', desc: 'Used to prevent heartworm disease and treat specific ear and skin mites.', price: 350 },
    { id: 'd3', subcategory: 'Antiparasitics', name: 'Pyrantel Pamoate', desc: 'Foundational dewormer used to eliminate intestinal roundworms and hookworms.', price: 200 },
    { id: 'd4', subcategory: 'Antiparasitics', name: 'Praziquantel', desc: 'Primary anti-parasitic treatment required to target and eradicate tapeworms.', price: 280 },
    { id: 'd5', subcategory: 'Antiparasitics', name: 'Fipronil', desc: 'Widely trusted topical spot-on solution used to eliminate fleas and ticks.', price: 450 },
    { id: 'd6', subcategory: 'Joint Care', name: 'Carprofen', desc: 'NSAID used safely for osteoarthritis pain and post-surgery recovery.', price: 550 },
    { id: 'd7', subcategory: 'Pain Care', name: 'Meloxicam', desc: 'Versatile NSAID to reduce pain, fever, and inflammation.', price: 420 },
    { id: 'd8', subcategory: 'Pain Care', name: 'Gabapentin', desc: 'Nerve-pain specialist utilized to manage chronic joint discomfort.', price: 380 },
    { id: 'd9', subcategory: 'Pain Care', name: 'Tramadol', desc: 'Opioid-like medication frequently prescribed to alleviate moderate acute pain.', price: 410 },
    { id: 'd10', subcategory: 'Joint Care', name: 'Prednisone', desc: 'Core systemic corticosteroid to suppress severe allergies.', price: 180 },
    { id: 'd11', subcategory: 'Antibiotics', name: 'Amoxicillin / Clavulanate', desc: 'Broad-spectrum antibiotic ideal for soft-tissue and skin infections.', price: 320 },
    { id: 'd12', subcategory: 'Antibiotics', name: 'Enrofloxacin', desc: 'Potent fluoroquinolone antibiotic reserved for severe, deep-seated infections.', price: 480 },
    { id: 'd13', subcategory: 'Antibiotics', name: 'Doxycycline', desc: 'Mandatory choice for treating tick-borne illnesses like Lyme disease.', price: 290 },
    { id: 'd14', subcategory: 'Antibiotics', name: 'Metronidazole', desc: 'Essential for treating anaerobic intestinal infections and Giardia.', price: 210 },
    { id: 'd15', subcategory: 'Antifungals', name: 'Ketoconazole', desc: 'Vital antifungal agents used to combat deep systemic or chronic ringworm.', price: 360 },
    { id: 'd16', subcategory: 'Gastrointestinal', name: 'Maropitant', desc: 'Veterinary-exclusive antiemetic medication used for motion sickness.', price: 950 },
    { id: 'd17', subcategory: 'Allergy', name: 'Oclacitinib', desc: 'Essential immunomodulator that targets and halts chronic itching.', price: 1200 },
    { id: 'd18', subcategory: 'Gastrointestinal', name: 'Famotidine', desc: 'H2-receptor antagonist commonly used to decrease stomach acid.', price: 150 },
    { id: 'd19', subcategory: 'Gastrointestinal', name: 'Sucralfate', desc: 'Mucosal protectant that functions like a band-aid to coat gastric ulcers.', price: 220 },
    { id: 'd20', subcategory: 'Heart', name: 'Pimobendan', desc: 'Critical inodilator that extends lifespan in dogs with heart failure.', price: 1400 },
    { id: 'd21', subcategory: 'Kidney', name: 'Furosemide', desc: 'Loop diuretic critical for clearing fluid backup in the lungs.', price: 140 },
    { id: 'd22', subcategory: 'Blood Pressure', name: 'Enalapril', desc: 'ACE inhibitors used to control high blood pressure.', price: 250 },
    { id: 'd23', subcategory: 'Sedatives', name: 'Phenobarbital', desc: 'Longest-standing maintenance medication to prevent epileptic seizures.', price: 310 },
    { id: 'd24', subcategory: 'Sedatives', name: 'Levetiracetam', desc: 'Modern anticonvulsant used to control sudden seizure episodes.', price: 580 },
    { id: 'd25', subcategory: 'Behavior', name: 'Acepromazine', desc: 'Foundational sedative used to calm dogs for veterinary procedures.', price: 190 },
    { id: 'd26', subcategory: 'Behavior', name: 'Trazodone', desc: 'Fast-acting behavior modifier used to manage acute anxiety.', price: 450 },
    { id: 'd27', subcategory: 'Emergency', name: 'Atropine', desc: 'Emergency injection used to treat dangerously low heart rates.', price: 170 },
    { id: 'd28', subcategory: 'Emergency', name: 'Apomorphine', desc: 'Fast-acting emetic utilized to safely induce vomiting after toxic ingestion.', price: 600 },
    { id: 'd29', subcategory: 'Topicals', name: 'Fludrocortisone', desc: 'Crucial hormone replacement for Addison\'s disease.', price: 850 },
    { id: 'd30', subcategory: 'Topicals', name: 'Miconazole + Chlorhexidine', desc: 'Medicated shampoo base to treat chronic bacterial and yeast skin infections.', price: 420 }
  ],
  cat: [
    { id: 'c1', subcategory: 'Parasite Control', name: 'Fluralaner', desc: 'Long-lasting topical spot-on medication used to eliminate fleas and ticks.', price: 950 },
    { id: 'c2', subcategory: 'Parasite Control', name: 'Selamectin', desc: 'Broad-spectrum topical covering fleas, heartworms, and ear mites.', price: 680 },
    { id: 'c3', subcategory: 'Parasite Control', name: 'Praziquantel', desc: 'Primary anti-parasitic explicitly required to eradicate tapeworms in felines.', price: 250 },
    { id: 'c4', subcategory: 'Parasite Control', name: 'Pyrantel Pamoate', desc: 'Safe oral liquid dewormer routinely given to kittens for roundworms.', price: 180 },
    { id: 'c5', subcategory: 'Pain Management', name: 'Meloxicam', desc: 'NSAID used for short-term post-operative pain or chronic arthritis.', price: 380 },
    { id: 'c6', subcategory: 'Pain Management', name: 'Frunevetmab', desc: 'Monthly monoclonal antibody injection for feline osteoarthritis.', price: 1800 },
    { id: 'c7', subcategory: 'Pain Management', name: 'Buprenorphine', desc: 'Partial opioid narcotic routinely used to control acute pain in cats.', price: 550 },
    { id: 'c8', subcategory: 'Pain Management', name: 'Gabapentin', desc: 'Versatile medication used to target neuropathic nerve pain.', price: 350 },
    { id: 'c9', subcategory: 'Antibiotics', name: 'Amoxicillin / Clavulanate', desc: 'Broad-spectrum antibiotic ideal for cat-bite abscesses and skin infections.', price: 300 },
    { id: 'c10', subcategory: 'Antibiotics', name: 'Doxycycline', desc: 'Primary choice for feline upper respiratory infections.', price: 280 },
    { id: 'c11', subcategory: 'Antibiotics', name: 'Cefovecin', desc: 'Long-acting, 14-day injectable cephalosporin antibiotic for difficult cats.', price: 1200 },
    { id: 'c12', subcategory: 'Antivirals', name: 'Famciclovir', desc: 'Systemic antiviral medication used specifically to treat feline herpesvirus.', price: 650 },
    { id: 'c13', subcategory: 'Organ Systems', name: 'Amlodipine', desc: 'Gold-standard first choice for treating severe feline hypertension.', price: 190 },
    { id: 'c14', subcategory: 'Organ Systems', name: 'Benazepril', desc: 'Medication used to manage feline Chronic Kidney Disease (CKD).', price: 240 },
    { id: 'c15', subcategory: 'Organ Systems', name: 'Methimazole', desc: 'Anti-thyroid drug given orally or as ear gel to treat hyperthyroidism.', price: 420 },
    { id: 'c16', subcategory: 'Organ Systems', name: 'Furosemide', desc: 'Crucial loop diuretic used to flush fluid buildup from the lungs.', price: 120 },
    { id: 'c17', subcategory: 'Organ Systems', name: 'Insulin Glargine', desc: 'Long-acting, life-saving injectable hormone for feline diabetes.', price: 1500 },
    { id: 'c18', subcategory: 'Gastrointestinal', name: 'Maropitant', desc: 'Highly effective antiemetic medication crucial for managing acute nausea.', price: 850 },
    { id: 'c19', subcategory: 'Gastrointestinal', name: 'Mirtazapine', desc: 'Appetite stimulant and anti-nausea treatment applied as an ear gel.', price: 410 },
    { id: 'c20', subcategory: 'Gastrointestinal', name: 'Ondansetron', desc: 'Powerful anti-emetic used in severe cases of vomiting.', price: 380 },
    { id: 'c21', subcategory: 'Gastrointestinal', name: 'Lactulose', desc: 'Oral osmotic stool softener essential for treating chronic feline constipation.', price: 200 },
    { id: 'c22', subcategory: 'Sedatives', name: 'Alfaxalone', desc: 'Modern, ultra-short-acting injectable anesthetic for safe sedation.', price: 700 },
    { id: 'c23', subcategory: 'Sedatives', name: 'Dexmedetomidine', desc: 'Powerful alpha-2 agonist sedative used for minor veterinary procedures.', price: 550 },
    { id: 'c24', subcategory: 'Sedatives', name: 'Atipamezole', desc: 'Emergency reversal agent to immediately wake cats up from sedatives.', price: 600 },
    { id: 'c25', subcategory: 'Behavior', name: 'Trazodone', desc: 'Fast-acting behavior modifier given to cats to alleviate vet-visit anxiety.', price: 380 },
    { id: 'c26', subcategory: 'Behavior', name: 'Diazepam', desc: 'Fast-acting benzodiazepine used primarily to halt active seizures.', price: 160 },
    { id: 'c27', subcategory: 'Topicals', name: 'Prednisolone', desc: 'Primary steroid used for cats to treat inflammatory bowel disease and asthma.', price: 210 },
    { id: 'c28', subcategory: 'Eyes', name: 'Terramycin', desc: 'Ophthalmic antibiotic ointment routinely used to heal conjunctivitis.', price: 320 },
    { id: 'c29', subcategory: 'Topicals', name: 'Chlorhexidine', desc: 'Antiseptic diluted to clean wounds or in wipes for feline acne.', price: 180 },
    { id: 'c30', subcategory: 'Supplements', name: 'Potassium Gluconate', desc: 'Oral supplement to treat low potassium seen in chronic kidney disease.', price: 250 }
  ],
  cow: [
    { id: 'cw1', subcategory: 'Antiparasitics', name: 'Albendazole', desc: 'Foundational oral dewormer bolus used to treat internal nematodes and liver flukes.', price: 150 },
    { id: 'cw2', subcategory: 'Antiparasitics', name: 'Fenbendazole', desc: 'Highly safe anthelmintic widely utilized to eradicate gastrointestinal roundworms.', price: 180 },
    { id: 'cw3', subcategory: 'Antiparasitics', name: 'Ivermectin', desc: 'Macrocyclic lactone available as an injection or pour-on to clear internal worms and mites.', price: 450 },
    { id: 'cw4', subcategory: 'Antiparasitics', name: 'Levamisole', desc: 'Fast-acting broad-spectrum dewormer that also acts as an immunostimulant.', price: 320 },
    { id: 'cw5', subcategory: 'Antiparasitics', name: 'Deltamethrin', desc: 'Vital topical spot-on or spray used to manage heavy tick, mite, and fly infestations.', price: 280 },
    { id: 'cw6', subcategory: 'Pain Management', name: 'Meloxicam', desc: 'Premier NSAID given to cattle to lower fevers and relieve pain from mastitis.', price: 350 },
    { id: 'cw7', subcategory: 'Anti-Inflammatories', name: 'Flunixin Meglumine', desc: 'Powerful NSAID chosen to combat shock caused by acute coliform mastitis.', price: 520 },
    { id: 'cw8', subcategory: 'Pain Management', name: 'Ketoprofen', desc: 'Versatile anti-inflammatory useful for managing downer cow syndrome.', price: 410 },
    { id: 'cw9', subcategory: 'Anti-Inflammatories', name: 'Dexamethasone', desc: 'Synthetic corticosteroid used to manage bovine ketosis and shock.', price: 200 },
    { id: 'cw10', subcategory: 'Antibiotics', name: 'Oxytetracycline', desc: 'Long-acting antibiotic deployed against shipping fever and foot rot.', price: 480 },
    { id: 'cw11', subcategory: 'Antibiotics', name: 'Ceftiofur', desc: 'Advanced cephalosporin antibiotic used to resolve severe respiratory complex.', price: 850 },
    { id: 'cw12', subcategory: 'Antibiotics', name: 'Amoxicillin', desc: 'Standard antibiotic commonly formulated as an intramammary infusion for mastitis.', price: 220 },
    { id: 'cw13', subcategory: 'Antibiotics', name: 'Cefalonium Dihydrate', desc: 'Essential long-acting antibiotic infused into the udder for dry cow therapy.', price: 600 },
    { id: 'cw14', subcategory: 'Antibiotics', name: 'Enrofloxacin', desc: 'Fluoroquinolone antibiotic reserved for stubborn bovine respiratory disease.', price: 720 },
    { id: 'cw15', subcategory: 'Rumen Care', name: 'Sodium Bicarbonate', desc: 'Critical rumen buffer given to rapidly correct acute carbohydrate engorgement.', price: 90 },
    { id: 'cw16', subcategory: 'Digestive', name: 'Poloxalene', desc: 'Premier surfactant anti-bloat agent used during life-threatening frothy pasture bloat.', price: 450 },
    { id: 'cw17', subcategory: 'Rumen Care', name: 'Magnesium Hydroxide', desc: 'Oral laxative and antacid powder used to treat simple ruminal indigestion.', price: 140 },
    { id: 'cw18', subcategory: 'Digestive', name: 'Liquid Paraffin', desc: 'Lubricating laxative administered via stomach tube to clear blockages.', price: 280 },
    { id: 'cw19', subcategory: 'Fluid Therapy', name: 'Calcium Gluconate', desc: 'Life-saving intravenous infusion used to instantly treat milk fever.', price: 350 },
    { id: 'cw20', subcategory: 'Metabolic', name: 'Magnesium Sulfate', desc: 'Rapidly corrects grass tetany (hypomagnesemia) in pastured cattle.', price: 160 },
    { id: 'cw21', subcategory: 'Fluid Therapy', name: 'Dextrose (50%)', desc: 'Intravenous sugar fluid used to directly treat clinical ketosis.', price: 220 },
    { id: 'cw22', subcategory: 'Metabolic', name: 'Oral Rehydration Salts', desc: 'Crucial electrolyte formulation to save scouring calves from dehydration.', price: 110 },
    { id: 'cw23', subcategory: 'Reproductive', name: 'Dinoprost', desc: 'Hormone injection used to synchronize estrus cycles or empty a retained uterus.', price: 580 },
    { id: 'cw24', subcategory: 'Hormonal', name: 'Buserelin Acetate', desc: 'Hormone used to treat ovarian cysts and boost herd conception rates.', price: 650 },
    { id: 'cw25', subcategory: 'Reproductive', name: 'Oxytocin', desc: 'Injectable hormone to stimulate contractions or assist with milk let-down.', price: 190 },
    { id: 'cw26', subcategory: 'Supportive Care', name: 'Xylazine', desc: 'Foundational sedative and muscle relaxant used to calm cattle down safely.', price: 320 },
    { id: 'cw27', subcategory: 'Supportive Care', name: 'Atropine Sulfate', desc: 'Antidote injection used to treat toxic organophosphate pesticide poisoning.', price: 210 },
    { id: 'cw28', subcategory: 'Supportive Care', name: 'Iodine Teat Dip', desc: 'Antiseptic formulated for post-milking teat dips to stop contagious mastitis.', price: 380 },
    { id: 'cw29', subcategory: 'Supportive Care', name: 'Calcium & Phosphorus Combo', desc: 'Nutritional supplements to support heavy milk production and bone health.', price: 550 },
    { id: 'cw30', subcategory: 'Supportive Care', name: 'Vitamin E & Selenium', desc: 'Injectable mineral blend vital for preventing white muscle disease in calves.', price: 420 }
  ]
};

const promotionalBanners = [
  { id: 1, tag: "Up to 20% off", bgClass: "bg-gradient-to-r from-red-50 to-white", tagClass: "bg-red-400 text-white", title: "First Move Final Mile", subtitle: "Premium Nutrition" },
  { id: 2, tag: "Up to 20% off", bgClass: "bg-gradient-to-r from-yellow-400 to-orange-400", tagClass: "bg-black/60 text-white", title: "50% MORE ENERGETIC", subtitle: "Feel the difference" },
  { id: 3, tag: "Flat 15% off", bgClass: "bg-gradient-to-br from-teal-500 to-emerald-600", tagClass: "bg-emerald-800 text-white", title: "Shield Your Best Buddy", subtitle: "Complete Tick Protection" },
  { id: 4, tag: "Buy 1 Get 1", bgClass: "bg-gradient-to-r from-purple-600 to-indigo-600", tagClass: "bg-indigo-900 text-white", title: "Jump Higher Purr Louder", subtitle: "Feline Joint Support" },
  { id: 5, tag: "Bulk Discount", bgClass: "bg-gradient-to-tr from-sky-500 to-blue-600", tagClass: "bg-blue-900 text-white", title: "Boost Yield & Vitality", subtitle: "Cow Calcium Supplements" },
  { id: 6, tag: "Save 30%", bgClass: "bg-gradient-to-bl from-rose-500 to-red-600", tagClass: "bg-red-900 text-white", title: "Daily Immunity Defense", subtitle: "Human Multi-vitamins" },
  { id: 7, tag: "New Arrival", bgClass: "bg-gradient-to-r from-orange-400 to-amber-500", tagClass: "bg-orange-900 text-white", title: "Heartworm Prevention", subtitle: "Keep their heart strong" },
  { id: 8, tag: "Special Care", bgClass: "bg-gradient-to-br from-fuchsia-600 to-pink-600", tagClass: "bg-fuchsia-900 text-white", title: "Feline Renal Support", subtitle: "Advanced kidney care" },
  { id: 9, tag: "10% off", bgClass: "bg-gradient-to-l from-emerald-500 to-green-600", tagClass: "bg-green-900 text-white", title: "Complete Deworming", subtitle: "Healthy herds better yield" },
  { id: 10, tag: "Essential", bgClass: "bg-gradient-to-r from-slate-800 to-slate-700", tagClass: "bg-teal-500 text-white", title: "First-Aid Essentials", subtitle: "Be prepared for emergencies" }
];

const faqsData = [
  { q: "How do I place an order?", a: "You can easily place an order by browsing our catalog, adding items to your cart, and proceeding to checkout. Alternatively, you can call our pharmacy directly at 9080386396 to place an order." },
  { q: "Do I need a prescription to buy medicines?", a: "For Schedule H and H1 drugs, a valid prescription from a registered medical practitioner is mandatory. You can upload it using our Drag and Drop feature on the home page." },
  { q: "How do I upload a prescription?", a: "Click on the 'Upload Prescription' card on the home page or simply drag and drop your file (JPG, PNG, or PDF) into the designated zone." },
  { q: "Why is my pincode not accepted?", a: "Currently, Parijatha Pharmaceuticals only supports delivery within Tamil Nadu. Please ensure you are entering a valid 6-digit Tamil Nadu pincode." },
  { q: "How much discount do I get?", a: "We offer competitive pricing where you can save up to 21% off MRP on select human and veterinary medicines." },
  { q: "Do you sell veterinary medicines?", a: "Yes! We have a comprehensive catalog of veterinary medicines specifically categorized for Dogs, Cats, and Cows." },
  { q: "Are your medicines authentic?", a: "Absolutely. We are a registered pharmacy (ESTD 1984) sourcing directly from authorized distributors and manufacturers. Quality and authenticity are guaranteed." },
  { q: "What payment methods do you accept?", a: "We accept Credit/Debit Cards, UPI (Google Pay, PhonePe, Paytm, etc.), and Cash on Delivery (COD)." },
  { q: "Is there a delivery fee?", a: "Delivery fees are calculated based on your location within Tamil Nadu and the size of your order. It will be displayed at checkout." },
  { q: "How can I track my order?", a: "Once your order is confirmed, our customer care team will keep you updated via phone/SMS regarding the dispatch and delivery status." },
  { q: "What is your return policy?", a: "We accept returns for unsealed, non-refrigerated medicines within 7 days of delivery. Refrigerated items (like insulin or vaccines) cannot be returned due to temperature control requirements." },
  { q: "Can I consult a pharmacist before buying?", a: "Yes, our expert pharmacists are available. Please call us at 9080386396 for guidance on dosage and alternatives." },
  { q: "Where is your physical store located?", a: "Our pharmacy is located at No 4, Devi Complex, Five Roads, Salem - 636 004, Tamil Nadu." },
  { q: "What are your business hours?", a: "We are open from 9:00 AM to 10:00 PM, Monday through Sunday." },
  { q: "Do you deliver outside Tamil Nadu?", a: "At this moment, our delivery services are strictly locked to Tamil Nadu to ensure fast and reliable service." },
  { q: "How do I order medicines for my farm/cows in bulk?", a: "You can use the quantity (Strips/Units) selector on the product card to add multiple items, or contact us via phone or email for bulk farm orders." },
  { q: "Can I cancel my order?", a: "Orders can be cancelled before they are dispatched. Please call customer care immediately if you wish to cancel." },
  { q: "What happens if an item I order is out of stock?", a: "If an item goes out of stock after you place an order, our pharmacist will call you to suggest an alternative brand with the same composition or process a refund." },
  { q: "Is my payment information secure?", a: "Yes, all digital transactions are processed through highly secure, bank-grade encrypted payment gateways." },
  { q: "How do I select the number of strips?", a: "Every medicine card has a quantity selector (- 1 +) right above the 'Add' button. Adjust the quantity before clicking Add." }
];

const ProductCard = ({ item, searchQuery, onAdd }) => {
  const [quantity, setQuantity] = useState(1);

  const increment = (e) => { e.stopPropagation(); setQuantity(q => q + 1); };
  const decrement = (e) => { e.stopPropagation(); setQuantity(q => (q > 1 ? q - 1 : 1)); };

  return (
    <div className="product-card bg-white/70 backdrop-blur-xl rounded-[2rem] shadow-lg shadow-slate-200/30 border border-white/60 hover:shadow-xl hover:-translate-y-1 hover:border-teal-200 transition-all duration-300 flex flex-col p-6 relative overflow-hidden group">
      <div className="flex flex-wrap gap-2 mb-4">
        {searchQuery.trim() && (
          <span className="flex items-center gap-1.5 px-2.5 py-1 bg-slate-900 text-white rounded-lg text-[9px] font-bold uppercase tracking-wider shadow-sm">
            {item.parentIcon} {item.parentCategory}
          </span>
        )}
        <span className="text-[9px] font-extrabold text-teal-700 uppercase tracking-widest bg-teal-50 px-2.5 py-1 rounded-lg border border-teal-100/50 shadow-sm">
          {item.subcategory}
        </span>
      </div>

      <h3 className="text-2xl font-black mb-2 text-slate-900 leading-tight tracking-tight group-hover:text-teal-700 transition-colors">{item.name}</h3>
      <p className="text-slate-500 text-sm mb-6 flex-grow leading-relaxed font-medium line-clamp-3">{item.desc}</p>
      
      <div className="flex flex-col gap-4 mt-auto pt-4 border-t border-slate-200/50">
        
        {/* Quantity Selector */}
        <div className="flex items-center justify-between bg-slate-50/80 p-2 rounded-xl border border-slate-100 shadow-inner">
           <button onClick={decrement} className="p-2 text-slate-400 hover:text-teal-600 bg-white rounded-lg shadow-sm border border-slate-200 transition-colors">
             <Minus className="w-4 h-4"/>
           </button>
           <span className="font-bold text-sm text-slate-700">
             {quantity} {quantity === 1 ? 'Strip' : 'Strips'}
           </span>
           <button onClick={increment} className="p-2 text-slate-400 hover:text-teal-600 bg-white rounded-lg shadow-sm border border-slate-200 transition-colors">
             <Plus className="w-4 h-4"/>
           </button>
        </div>
        
        <div className="flex justify-between items-center">
          <div className="flex flex-col">
            <span className="text-[10px] text-slate-400 font-bold uppercase tracking-widest mb-1">MRP Price</span>
            <span className="text-2xl font-black text-slate-900 tracking-tight">₹{item.price}</span>
          </div>
          <button 
            onClick={(e) => { 
              e.stopPropagation(); 
              onAdd(item, e, quantity); 
              setQuantity(1);
            }} 
            className="bg-white border border-slate-200 text-slate-900 hover:bg-teal-600 hover:border-teal-600 hover:text-white px-4 py-2.5 flex items-center gap-2 rounded-xl font-bold transition-all shadow-sm"
          >
            <Plus className="w-4 h-4" /> Add
          </button>
        </div>
      </div>
    </div>
  );
};

export default function ParijathaApp() {
  const [activeSection, setActiveSection] = useState('human');
  const [searchQuery, setSearchQuery] = useState('');
  const [cart, setCart] = useState([]);
  const [view, setView] = useState('shop'); 
  
  const [prescriptionFile, setPrescriptionFile] = useState(null);
  const [isDragging, setIsDragging] = useState(false);
  const [activeFaq, setActiveFaq] = useState(null);
  
  const cartRef = useRef(null);
  const [animatingCards, setAnimatingCards] = useState([]);
  
  const [addressData, setAddressData] = useState({
    name: '', phone: '', street: '', pincode: '', city: 'Malayadipudur', state: 'Tamil Nadu', tag: 'home'
  });
  const [pincodeLoading, setPincodeLoading] = useState(false);
  const [pincodeError, setPincodeError] = useState('');
  const [paymentMethod, setPaymentMethod] = useState('');
  const [checkoutError, setCheckoutError] = useState('');

  useEffect(() => {
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }, [view]);

  const sections = [
    { id: 'human', label: 'Human Care', icon: <HeartPulse className="w-5 h-5" /> },
    { id: 'dog', label: 'Dog Care', icon: <Dog className="w-5 h-5" /> },
    { id: 'cat', label: 'Cat Care', icon: <Cat className="w-5 h-5" /> },
    { id: 'cow', label: 'Cow Care', icon: <Tractor className="w-5 h-5" /> }
  ];

  const allProducts = useMemo(() => {
    const flatten = (categoryKey, label, icon) => 
      inventoryData[categoryKey].map(item => ({
        ...item, parentCategory: label, parentIcon: icon, categoryId: categoryKey
      }));
    return [
      ...flatten('human', 'Human Care', <HeartPulse className="w-3 h-3" />),
      ...flatten('dog', 'Dog Care', <Dog className="w-3 h-3" />),
      ...flatten('cat', 'Cat Care', <Cat className="w-3 h-3" />),
      ...flatten('cow', 'Cow Care', <Tractor className="w-3 h-3" />)
    ];
  }, []);

  const searchResults = useMemo(() => {
    if (!searchQuery.trim()) return [];
    const query = searchQuery.toLowerCase();
    return allProducts.filter(item => 
      item.name.toLowerCase().includes(query) || 
      item.subcategory.toLowerCase().includes(query) ||
      item.desc.toLowerCase().includes(query)
    );
  }, [searchQuery, allProducts]);

  const displayedProducts = useMemo(() => {
    if (searchQuery.trim()) return searchResults;
    return inventoryData[activeSection].map(item => ({
      ...item,
      parentCategory: sections.find(s => s.id === activeSection)?.label,
      parentIcon: sections.find(s => s.id === activeSection)?.icon
    }));
  }, [searchQuery, searchResults, activeSection, sections]);

  const handleAddToCart = (item, e, quantityToAdd = 1) => {
    e.stopPropagation();
    
    if (cartRef.current) {
      const cardEl = e.currentTarget.closest('.product-card');
      if (cardEl) {
        const cardRect = cardEl.getBoundingClientRect();
        const cartRect = cartRef.current.getBoundingClientRect();
        
        const startX = cardRect.left;
        const startY = cardRect.top;
        const targetX = cartRect.left + cartRect.width / 2 - (startX + cardRect.width / 2);
        const targetY = cartRect.top + cartRect.height / 2 - (startY + cardRect.height / 2);

        const animId = Date.now() + Math.random();
        
        setAnimatingCards(prev => [...prev, {
          id: animId,
          item,
          qtyAdded: quantityToAdd,
          rect: cardRect,
          tx: targetX,
          ty: targetY
        }]);

        setTimeout(() => {
          setAnimatingCards(prev => prev.filter(anim => anim.id !== animId));
          setCart(prev => {
            const existing = prev.find(p => p.id === item.id);
            if (existing) return prev.map(p => p.id === item.id ? { ...p, qty: p.qty + quantityToAdd } : p);
            return [...prev, { ...item, qty: quantityToAdd }];
          });
        }, 800);
        return;
      }
    }

    setCart(prev => {
      const existing = prev.find(p => p.id === item.id);
      if (existing) return prev.map(p => p.id === item.id ? { ...p, qty: p.qty + quantityToAdd } : p);
      return [...prev, { ...item, qty: quantityToAdd }];
    });
  };

  const updateQuantity = (id, delta) => {
    setCart(prev => prev.map(item => {
      if (item.id === id) {
        const newQty = Math.max(1, item.qty + delta);
        return { ...item, qty: newQty };
      }
      return item;
    }).filter(item => item.qty > 0));
  };

  const removeFromCart = (id) => setCart(prev => prev.filter(item => item.id !== id));
  const cartItemCount = cart.reduce((sum, item) => sum + item.qty, 0);
  const totalAmount = cart.reduce((sum, item) => sum + (item.price * item.qty), 0);

  const handleDragOver = useCallback((e) => { e.preventDefault(); setIsDragging(true); }, []);
  const handleDragLeave = useCallback((e) => { e.preventDefault(); setIsDragging(false); }, []);
  const handleDrop = useCallback((e) => {
    e.preventDefault(); setIsDragging(false);
    if (e.dataTransfer.files && e.dataTransfer.files.length > 0) setPrescriptionFile(e.dataTransfer.files[0]);
  }, []);
  
  useEffect(() => {
    const fetchDistrict = async () => {
      if (addressData.pincode.length === 6) {
        setPincodeLoading(true); setPincodeError('');
        try {
          const response = await fetch(`https://api.postalpincode.in/pincode/${addressData.pincode}`);
          const data = await response.json();
          if (data && data[0].Status === 'Success') {
            setAddressData(prev => ({ ...prev, city: data[0].PostOffice[0].District }));
          } else {
            setPincodeError('Invalid Pincode.');
          }
        } catch (err) {
          setPincodeError('Network error checking pincode.');
        } finally {
          setPincodeLoading(false);
        }
      }
    };
    const timeoutId = setTimeout(fetchDistrict, 500);
    return () => clearTimeout(timeoutId);
  }, [addressData.pincode]);

  const handleAddressChange = (e) => {
    const { name, value } = e.target;
    if (name === 'pincode' || name === 'phone') {
      const maxLen = name === 'pincode' ? 6 : 10;
      setAddressData(prev => ({ ...prev, [name]: value.replace(/\D/g, '').slice(0, maxLen) }));
    } else {
      setAddressData(prev => ({ ...prev, [name]: value }));
    }
  };

  const validateAndProceedToPayment = () => {
    if (!addressData.name || !addressData.phone || !addressData.street || !addressData.pincode || !addressData.city) {
      setCheckoutError("Please fill out all required fields.");
      return;
    }
    if (addressData.pincode.length !== 6) return setCheckoutError("Please enter a valid 6-digit pincode.");
    if (addressData.phone.length !== 10) return setCheckoutError("Please enter a valid 10-digit phone number.");
    setCheckoutError('');
    setView('checkout');
  };

  const finalizeOrder = () => {
    if (!paymentMethod) return setCheckoutError("Please select a payment method.");
    setCheckoutError('');
    setCart([]); setPaymentMethod(''); setPrescriptionFile(null);
    setView('success');
  };

  return (
    <div className="min-h-screen bg-white font-sans text-slate-800 selection:bg-teal-200">
      
      <style>
        {`
          @keyframes marquee {
            0% { transform: translateX(0); }
            100% { transform: translateX(-50%); }
          }
          .animate-marquee {
            animation: marquee 40s linear infinite;
          }
          .animate-marquee:hover {
            animation-play-state: paused;
          }
          
          @keyframes flyCardFull {
            0% {
              transform: translate(0, 0) scale(1);
              opacity: 1;
            }
            15% {
              transform: translate(0, -30px) scale(1.02);
              opacity: 1;
              box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
            }
            100% {
              transform: translate(var(--tx), var(--ty)) scale(0.05);
              opacity: 0;
            }
          }
          .anim-card {
            animation: flyCardFull 0.8s cubic-bezier(0.25, 1, 0.5, 1) forwards;
            position: fixed;
            z-index: 9999;
            pointer-events: none;
            will-change: transform, opacity;
          }
        `}
      </style>

      <header className="relative z-40 bg-white/40 backdrop-blur-2xl border-b border-white/60 shadow-[0_8px_32px_0_rgba(31,38,135,0.07)] transition-all duration-300">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-3 flex flex-wrap justify-between items-center gap-4">
          
          <div className="flex items-center gap-4 cursor-pointer group" onClick={() => { setView('shop'); setSearchQuery(''); }}>
            <div className="bg-teal-600 text-white w-10 h-10 rounded-xl flex items-center justify-center shadow-lg group-hover:bg-teal-500 transition-colors">
              <Pill className="w-5 h-5" />
            </div>
            <div>
              <h1 className="text-xl sm:text-2xl font-black tracking-widest text-slate-900 uppercase leading-none">PARIJATHA</h1>
              <h2 className="text-teal-600 text-[10px] sm:text-xs font-bold tracking-[0.25em] mt-1 uppercase">PHARMACEUTICALS</h2>
            </div>
          </div>
          
          <nav className="hidden md:flex items-center gap-2 bg-white/30 backdrop-blur-sm rounded-full p-1 border border-white/50 shadow-inner">
            <button 
              onClick={() => { setView('shop'); setSearchQuery(''); }}
              className={`px-5 py-2 rounded-full font-bold text-sm transition-all ${view === 'shop' ? 'bg-white shadow-md text-teal-700' : 'text-slate-600 hover:bg-white/50 hover:text-slate-900'}`}
            >
              Home
            </button>
            <button 
              onClick={() => setView('faq')}
              className={`px-5 py-2 rounded-full font-bold text-sm transition-all ${view === 'faq' ? 'bg-white shadow-md text-teal-700' : 'text-slate-600 hover:bg-white/50 hover:text-slate-900'}`}
            >
              FAQ
            </button>
            <button 
              onClick={() => setView('contact')}
              className={`px-5 py-2 rounded-full font-bold text-sm transition-all ${view === 'contact' ? 'bg-white shadow-md text-teal-700' : 'text-slate-600 hover:bg-white/50 hover:text-slate-900'}`}
            >
              Contact Us
            </button>
          </nav>

          <button 
            ref={cartRef}
            onClick={() => setView('cart')}
            className="flex items-center gap-3 bg-white/70 hover:bg-white border border-white/80 px-5 py-2.5 rounded-2xl shadow-[0_4px_12px_rgba(0,0,0,0.05)] hover:shadow-md transition-all relative group"
          >
            <div className="relative">
              <ShoppingCart className="w-5 h-5 text-slate-700 group-hover:text-teal-600 transition-colors" />
              {cartItemCount > 0 && (
                <span className="absolute -top-2 -right-2 bg-teal-600 text-white text-[10px] font-bold px-1.5 py-0.5 rounded-full min-w-[18px] text-center shadow-sm">
                  {cartItemCount}
                </span>
              )}
            </div>
            <div className="hidden sm:flex flex-col items-start">
              <span className="text-[10px] font-bold text-slate-500 uppercase tracking-widest leading-none mb-1">Total</span>
              <span className="font-extrabold text-sm leading-none text-slate-900">₹{totalAmount}</span>
            </div>
          </button>
        </div>
      </header>

      {/* FLYING CARD ANIMATION PORTALS */}
      {animatingCards.map(anim => (
        <div
          key={anim.id}
          className="anim-card bg-white/90 backdrop-blur-xl rounded-[2rem] shadow-2xl border border-teal-200 flex flex-col p-6 overflow-hidden"
          style={{
            left: anim.rect.left, top: anim.rect.top, width: anim.rect.width, height: anim.rect.height,
            '--tx': `${anim.tx}px`, '--ty': `${anim.ty}px`
          }}
        >
          <div className="flex flex-wrap gap-2 mb-4">
            <span className="text-[9px] font-extrabold text-teal-700 uppercase tracking-widest bg-teal-50 px-2.5 py-1 rounded-lg border border-teal-100/50 shadow-sm">
              {anim.item.subcategory}
            </span>
          </div>
          <h3 className="text-2xl font-black mb-2 text-slate-900 leading-tight tracking-tight">{anim.item.name}</h3>
          <p className="text-slate-500 text-sm mb-6 flex-grow leading-relaxed font-medium line-clamp-3">{anim.item.desc}</p>
          <div className="flex flex-col gap-4 mt-auto pt-4 border-t border-slate-200/50">
            <div className="flex justify-between items-center">
              <div className="flex flex-col">
                <span className="text-[10px] text-slate-400 font-bold uppercase tracking-widest mb-1">Added</span>
                <span className="text-xl font-black text-teal-700 tracking-tight">{anim.qtyAdded} {anim.qtyAdded === 1 ? 'Strip' : 'Strips'}</span>
              </div>
              <button className="bg-teal-600 border border-teal-600 text-white px-4 py-2.5 flex items-center gap-2 rounded-xl font-bold transition-all shadow-sm">
                <CheckCircle className="w-4 h-4" /> Done
              </button>
            </div>
          </div>
        </div>
      ))}

      <main className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 sm:py-12">
        
        {}
        {view === 'shop' && (
          <div className="animate-in fade-in duration-500">
            
            <div className="text-center mb-10 pt-4 pb-8">
              <h2 className="text-2xl sm:text-3xl font-black text-slate-800 tracking-tight mb-2">
                Say GoodBye to high medicine prices
              </h2>
              <p className="text-sm sm:text-base font-medium text-slate-500">
                Compare prices and save up to 21%
              </p>
            </div>

            <div className="mb-8 w-full flex items-center justify-center gap-4 sm:gap-8">
              <div className="h-px bg-gradient-to-r from-transparent to-slate-300 flex-grow max-w-[150px]"></div>
              <h3 className="text-sm sm:text-xl font-black text-slate-800 tracking-widest uppercase text-center shrink-0">
                ORDER MEDICINES VIA
              </h3>
              <div className="h-px bg-gradient-to-l from-transparent to-slate-300 flex-grow max-w-[150px]"></div>
            </div>

            <div className="grid grid-cols-1 md:grid-cols-2 gap-6 mb-12">
              <div 
                onDragOver={handleDragOver} onDragLeave={handleDragLeave} onDrop={handleDrop}
                className={`border border-white/40 bg-white/60 backdrop-blur-md rounded-[2rem] p-8 sm:p-10 flex flex-col items-center justify-center text-center transition-all duration-300 relative overflow-hidden group shadow-lg ${
                  isDragging ? 'ring-2 ring-teal-500 bg-teal-50/50 scale-[1.01]' : 'hover:bg-white/90 hover:shadow-xl'
                }`}
              >
                <input type="file" id="prescription" className="hidden" onChange={(e) => setPrescriptionFile(e.target.files[0])} accept=".jpg,.jpeg,.png,.pdf" />
                <div className={`w-16 h-16 rounded-2xl flex items-center justify-center mb-5 transition-colors shadow-inner ${prescriptionFile ? 'bg-teal-100 text-teal-600' : 'bg-slate-100 text-slate-500 group-hover:bg-teal-50 group-hover:text-teal-600'}`}>
                  {prescriptionFile ? <FileText className="w-8 h-8" /> : <UploadCloud className="w-8 h-8" />}
                </div>
                <h3 className="text-xl sm:text-2xl font-black text-slate-800 mb-2">{prescriptionFile ? 'Prescription Attached' : 'Upload Prescription'}</h3>
                <p className="text-slate-500 font-medium mb-6 max-w-sm text-sm sm:text-base">
                  {prescriptionFile ? <span className="text-teal-700 font-bold">{prescriptionFile.name}</span> : 'Drag and drop your prescription file here.'}
                </p>
                <label htmlFor="prescription" className="cursor-pointer inline-flex items-center justify-center font-bold py-3 px-8 rounded-xl bg-slate-900 text-white hover:bg-teal-600 transition-all shadow-md">
                  {prescriptionFile ? 'Replace File' : 'Browse Files'}
                </label>
              </div>

              <div className="border border-white/40 bg-white/60 backdrop-blur-md rounded-[2rem] p-8 sm:p-10 flex flex-col items-center justify-center text-center transition-all duration-300 shadow-lg hover:bg-white/90 hover:shadow-xl">
                <div className="w-16 h-16 rounded-2xl flex items-center justify-center mb-5 bg-teal-50 text-teal-600 shadow-inner">
                  <PhoneCall className="w-8 h-8" />
                </div>
                <h3 className="text-xl sm:text-2xl font-black text-slate-800 mb-2">Call to order</h3>
                <p className="text-slate-500 font-medium mb-6 max-w-sm text-sm sm:text-base">
                  Speak directly with our pharmacists to place your order instantly.
                </p>
                <a href="tel:9080386396" className="inline-flex items-center justify-center gap-2 font-bold py-3 px-8 rounded-xl bg-slate-900 text-white hover:bg-teal-600 transition-all shadow-md">
                  <Phone className="w-5 h-5" /> 9080386396
                </a>
              </div>
            </div>

            <div className="overflow-hidden w-full relative mb-12 rounded-[2rem] shadow-sm">
              <div className="flex w-max animate-marquee hover:[animation-play-state:paused] gap-6 px-3">
                {[...promotionalBanners, ...promotionalBanners].map((banner, index) => (
                  <div key={`${banner.id}-${index}`} className={`w-[350px] sm:w-[450px] h-[200px] rounded-[2rem] relative overflow-hidden flex items-center p-8 shrink-0 ${banner.bgClass} shadow-inner`}>
                    <div className={`absolute top-0 left-0 px-4 py-1.5 rounded-br-xl font-bold text-xs uppercase tracking-widest shadow-sm z-20 ${banner.tagClass}`}>
                      {banner.tag}
                    </div>
                    <div className="relative z-10 w-full text-left">
                       <h3 className={`text-3xl sm:text-4xl font-black leading-tight tracking-tight mb-2 ${banner.id === 1 ? 'text-slate-800' : 'text-white'}`}>{banner.title}</h3>
                       <p className={`font-bold uppercase tracking-widest text-sm ${banner.id === 1 ? 'text-slate-500' : 'text-white/80'}`}>{banner.subtitle}</p>
                    </div>
                  </div>
                ))}
              </div>
            </div>

            <div className="relative mb-8 max-w-3xl mx-auto z-20">
              <div className="absolute inset-y-0 left-0 pl-6 flex items-center pointer-events-none">
                <Search className="w-6 h-6 text-teal-500" />
              </div>
              <input 
                type="text" 
                value={searchQuery}
                onChange={(e) => setSearchQuery(e.target.value)}
                placeholder="Search across all 120 medicines..." 
                className="w-full pl-16 pr-14 py-5 bg-white/80 backdrop-blur-md border border-white/40 rounded-[2rem] text-lg font-bold text-slate-800 focus:outline-none focus:ring-4 focus:ring-teal-500/20 shadow-lg placeholder:text-slate-400 placeholder:font-medium transition-all"
              />
              {searchQuery && (
                <button onClick={() => setSearchQuery('')} className="absolute inset-y-0 right-0 pr-6 flex items-center text-slate-400 hover:text-slate-600">
                  <div className="bg-slate-100 p-2 rounded-full"><X className="w-4 h-4" /></div>
                </button>
              )}
            </div>

            {!searchQuery.trim() && (
              <div className="flex gap-4 mb-8 overflow-x-auto pb-4 scrollbar-hide snap-x">
                {sections.map(section => (
                  <button key={section.id} onClick={() => setActiveSection(section.id)} className={`snap-start flex items-center gap-3 px-8 py-4 rounded-2xl font-bold transition-all whitespace-nowrap shadow-sm text-sm sm:text-base border ${activeSection === section.id ? 'bg-slate-900 border-slate-900 text-white shadow-lg' : 'bg-white/60 border-white/40 text-slate-600 hover:bg-white backdrop-blur-sm'}`}>
                    <div className={`${activeSection === section.id ? 'text-teal-400' : 'text-slate-400'}`}>{section.icon}</div>
                    {section.label}
                  </button>
                ))}
              </div>
            )}

            <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6">
              {displayedProducts.map((item, idx) => (
                <ProductCard 
                  key={`${item.id}-${idx}`} 
                  item={item}
                  searchQuery={searchQuery}
                  onAdd={handleAddToCart}
                />
              ))}
            </div>
          </div>
        )}

        {}
        {view === 'faq' && (
          <div className="max-w-4xl mx-auto animate-in slide-in-from-bottom-4 duration-500">
             <div className="text-center mb-12">
               <div className="inline-flex items-center justify-center w-16 h-16 rounded-2xl bg-teal-100 text-teal-600 mb-6 shadow-inner">
                 <HelpCircle className="w-8 h-8" />
               </div>
               <h2 className="text-4xl font-black text-slate-900 tracking-tight mb-4">Frequently Asked Questions</h2>
               <p className="text-lg text-slate-500 font-medium">Everything you need to know about ordering, shipping, and our pharmacy.</p>
             </div>
             
             <div className="space-y-4">
               {faqsData.map((faq, idx) => (
                 <div key={idx} className="bg-white/70 backdrop-blur-md border border-slate-200/60 rounded-2xl overflow-hidden shadow-sm hover:shadow-md transition-all">
                   <button 
                     onClick={() => setActiveFaq(activeFaq === idx ? null : idx)}
                     className="w-full text-left px-6 py-5 flex justify-between items-center focus:outline-none group"
                   >
                     <span className={`font-bold text-lg transition-colors ${activeFaq === idx ? 'text-teal-700' : 'text-slate-800 group-hover:text-teal-600'}`}>
                       {faq.q}
                     </span>
                     <ChevronDown className={`w-5 h-5 text-slate-400 transition-transform duration-300 ${activeFaq === idx ? 'rotate-180 text-teal-600' : ''}`} />
                   </button>
                   <div 
                     className="grid transition-all duration-300 ease-in-out"
                     style={{ gridTemplateRows: activeFaq === idx ? '1fr' : '0fr' }}
                   >
                     <div className="overflow-hidden">
                       <p className="px-6 pb-5 pt-1 text-slate-600 font-medium leading-relaxed">
                         {faq.a}
                       </p>
                     </div>
                   </div>
                 </div>
               ))}
             </div>
          </div>
        )}

        {}
        {view === 'contact' && (
          <div className="max-w-5xl mx-auto animate-in slide-in-from-bottom-4 duration-500">
            <div className="text-center mb-12">
               <div className="inline-flex items-center justify-center w-16 h-16 rounded-2xl bg-teal-100 text-teal-600 mb-6 shadow-inner">
                 <Info className="w-8 h-8" />
               </div>
               <h2 className="text-4xl font-black text-slate-900 tracking-tight mb-4">Get in Touch</h2>
               <p className="text-lg text-slate-500 font-medium">We're here to help with your prescriptions and orders.</p>
            </div>

            <div className="grid grid-cols-1 md:grid-cols-2 gap-8">
              
              <div className="bg-white/80 backdrop-blur-xl border border-white/60 p-10 rounded-[2.5rem] shadow-xl flex flex-col gap-8 hover:shadow-2xl transition-all">
                <div className="flex items-start gap-5">
                  <div className="p-4 bg-teal-50 rounded-2xl text-teal-600 border border-teal-100 shadow-sm"><Phone className="w-7 h-7" /></div>
                  <div>
                    <h4 className="text-sm font-bold uppercase tracking-widest text-slate-400 mb-1">Call Us Directly</h4>
                    <a href="tel:9080386396" className="text-3xl font-black text-slate-900 hover:text-teal-600 transition-colors">9080386396</a>
                  </div>
                </div>
                <div className="w-full h-px bg-slate-200/60"></div>
                
                <div className="flex items-start gap-5">
                  <div className="p-4 bg-teal-50 rounded-2xl text-teal-600 border border-teal-100 shadow-sm"><Mail className="w-7 h-7" /></div>
                  <div>
                    <h4 className="text-sm font-bold uppercase tracking-widest text-slate-400 mb-1">Email Support</h4>
                    <a href="mailto:ppprashanth13@yahoo.com" className="text-xl font-bold text-slate-900 hover:text-teal-600 transition-colors break-all">ppprashanth13@yahoo.com</a>
                  </div>
                </div>
                <div className="w-full h-px bg-slate-200/60"></div>
                
                <div className="flex items-start gap-5">
                  <div className="p-4 bg-teal-50 rounded-2xl text-teal-600 border border-teal-100 shadow-sm"><Clock className="w-7 h-7" /></div>
                  <div>
                    <h4 className="text-sm font-bold uppercase tracking-widest text-slate-400 mb-1">Business Hours</h4>
                    <p className="text-lg font-bold text-slate-900">Monday - Sunday</p>
                    <p className="text-slate-500 font-medium">9:00 AM - 10:00 PM</p>
                  </div>
                </div>
              </div>

              <div className="bg-slate-900 text-white p-10 rounded-[2.5rem] shadow-xl flex flex-col items-center text-center gap-6 justify-center relative overflow-hidden">
                <div className="absolute top-0 left-0 w-full h-full bg-gradient-to-br from-teal-900/20 to-transparent pointer-events-none"></div>
                <div className="p-5 bg-white/10 rounded-3xl border border-white/20 backdrop-blur-md mb-2">
                  <MapPin className="w-10 h-10 text-teal-400" />
                </div>
                <h3 className="text-2xl font-black uppercase tracking-widest text-teal-400">Parijatha Pharmaceuticals</h3>
                <p className="text-xl font-medium text-slate-300 leading-relaxed max-w-sm">
                  No 4, Devi Complex,<br/>
                  Five Roads, Salem - 636 004<br/>
                  Tamil Nadu, India.
                </p>
              </div>

            </div>
          </div>
        )}

        {}
        {view === 'cart' && (
          <div className="max-w-4xl mx-auto animate-in slide-in-from-bottom-4 duration-300">
            <button onClick={() => setView('shop')} className="flex items-center gap-2 text-slate-500 hover:text-teal-700 mb-6 font-bold text-sm uppercase tracking-wider group">
              <ArrowLeft className="w-4 h-4 group-hover:-translate-x-1 transition-transform" /> Continue Shopping
            </button>
            <div className="bg-white/80 backdrop-blur-xl p-8 sm:p-12 rounded-[2.5rem] shadow-xl border border-white/60">
              <h2 className="text-3xl font-black text-slate-900 mb-8 pb-6 border-b border-slate-200/60 flex items-center gap-4">
                <ShoppingCart className="w-8 h-8 text-teal-600" /> Review Cart
              </h2>
              {cart.length === 0 ? (
                <div className="text-center py-16">
                  <p className="text-slate-500 text-xl font-medium mb-6">Your cart is empty.</p>
                  <button onClick={() => setView('shop')} className="bg-slate-900 text-white px-8 py-4 rounded-xl font-bold hover:bg-teal-600 transition-colors">Browse Catalog</button>
                </div>
              ) : (
                <>
                  <div className="space-y-4 mb-8">
                    {cart.map(item => (
                      <div key={item.id} className="flex flex-col sm:flex-row justify-between items-center p-6 bg-white border border-slate-100 rounded-3xl shadow-sm gap-6">
                        <div className="flex-1 text-center sm:text-left">
                          <h4 className="font-bold text-xl text-slate-900 mb-1">{item.name}</h4>
                          <span className="text-[10px] font-extrabold text-slate-400 uppercase tracking-widest">{item.subcategory}</span>
                        </div>
                        <div className="flex items-center gap-6">
                          <div className="flex items-center gap-4 bg-slate-50 p-2 rounded-xl border border-slate-200">
                            <button onClick={() => updateQuantity(item.id, -1)} className="p-1 hover:text-teal-600"><Minus className="w-4 h-4" /></button>
                            <span className="w-4 text-center font-bold">{item.qty}</span>
                            <button onClick={() => updateQuantity(item.id, 1)} className="p-1 hover:text-teal-600"><Plus className="w-4 h-4" /></button>
                          </div>
                          <span className="font-black text-2xl w-24 text-right">₹{item.price * item.qty}</span>
                          <button onClick={() => removeFromCart(item.id)} className="text-slate-300 hover:text-red-500"><Trash2 className="w-5 h-5" /></button>
                        </div>
                      </div>
                    ))}
                  </div>
                  <div className="bg-slate-900 text-white rounded-[2rem] p-8 flex flex-col sm:flex-row justify-between items-center shadow-lg">
                    <div>
                      <span className="text-slate-400 text-sm font-bold uppercase tracking-widest">Grand Total</span>
                      <div className="text-4xl font-black">₹{totalAmount}</div>
                    </div>
                    <button onClick={() => setView('address')} className="mt-6 sm:mt-0 px-10 py-4 bg-teal-500 text-slate-900 hover:bg-teal-400 rounded-xl font-bold flex items-center gap-2 transition-colors">
                      Proceed to Delivery <ChevronRight className="w-5 h-5" />
                    </button>
                  </div>
                </>
              )}
            </div>
          </div>
        )}

        {}
        {view === 'address' && (
          <div className="max-w-3xl mx-auto animate-in slide-in-from-right-4 duration-300">
            <button onClick={() => setView('cart')} className="flex items-center gap-2 text-slate-500 hover:text-teal-700 mb-6 font-bold text-sm uppercase tracking-wider group">
              <ArrowLeft className="w-4 h-4 group-hover:-translate-x-1 transition-transform" /> Back to Cart
            </button>
            <div className="bg-white/80 backdrop-blur-xl p-8 sm:p-12 rounded-[2.5rem] shadow-xl border border-white/60">
              <h2 className="text-3xl font-black text-slate-900 mb-2 flex items-center gap-4"><MapPin className="text-teal-600" /> Delivery Details</h2>
              <p className="text-slate-500 font-medium mb-8 pb-6 border-b border-slate-200">Where should we deliver your order?</p>
              
              {checkoutError && <div className="mb-6 p-4 bg-red-50 text-red-600 font-bold rounded-xl border border-red-100">{checkoutError}</div>}
              
              <div className="grid grid-cols-1 md:grid-cols-2 gap-6 mb-8">
                <div className="col-span-1 md:col-span-2">
                  <label className="block text-xs font-bold text-slate-500 uppercase tracking-widest mb-2">Full Name</label>
                  <input type="text" name="name" value={addressData.name} onChange={handleAddressChange} className="w-full p-4 bg-white border border-slate-200 rounded-xl font-bold focus:border-teal-500 outline-none" />
                </div>
                <div className="col-span-1 md:col-span-2">
                  <label className="block text-xs font-bold text-slate-500 uppercase tracking-widest mb-2">Phone Number</label>
                  <input type="text" name="phone" value={addressData.phone} onChange={handleAddressChange} maxLength="10" className="w-full p-4 bg-white border border-slate-200 rounded-xl font-bold focus:border-teal-500 outline-none" />
                </div>
                <div className="col-span-1 md:col-span-2">
                  <label className="block text-xs font-bold text-slate-500 uppercase tracking-widest mb-2">Street Address</label>
                  <input type="text" name="street" value={addressData.street} onChange={handleAddressChange} className="w-full p-4 bg-white border border-slate-200 rounded-xl font-bold focus:border-teal-500 outline-none" />
                </div>
                <div>
                  <label className="flex text-xs font-bold text-slate-500 uppercase tracking-widest mb-2 justify-between">
                    Pincode {pincodeLoading && <Loader2 className="w-3 h-3 animate-spin" />}
                  </label>
                  <input type="text" name="pincode" value={addressData.pincode} onChange={handleAddressChange} maxLength="6" className={`w-full p-4 bg-white border ${pincodeError ? 'border-red-400' : 'border-slate-200'} rounded-xl font-bold focus:border-teal-500 outline-none tracking-widest`} />
                  {pincodeError && <span className="text-[10px] text-red-500 font-bold mt-1 block">{pincodeError}</span>}
                </div>
                <div>
                  <label className="block text-xs font-bold text-slate-500 uppercase tracking-widest mb-2">City / District</label>
                  <input type="text" name="city" value={addressData.city} readOnly className="w-full p-4 bg-slate-50 border border-slate-200 rounded-xl font-bold text-slate-700 cursor-not-allowed" />
                </div>
                <div className="col-span-1 md:col-span-2">
                  <label className="block text-xs font-bold text-slate-500 uppercase tracking-widest mb-2">State</label>
                  <div className="w-full p-4 bg-slate-50 border border-slate-200 rounded-xl font-bold text-slate-500 flex justify-between items-center cursor-not-allowed">
                    Tamil Nadu <span className="text-[10px] bg-slate-200 px-2 py-0.5 rounded uppercase">Locked</span>
                  </div>
                </div>
              </div>
              <button onClick={validateAndProceedToPayment} className="w-full py-5 rounded-xl font-bold bg-slate-900 text-white hover:bg-teal-600 transition-colors text-lg shadow-lg">
                Proceed to Payment
              </button>
            </div>
          </div>
        )}

        {}
        {view === 'checkout' && (
          <div className="max-w-2xl mx-auto animate-in slide-in-from-right-4 duration-300">
            <button onClick={() => setView('address')} className="flex items-center gap-2 text-slate-500 hover:text-teal-700 mb-6 font-bold text-sm uppercase tracking-wider group">
              <ArrowLeft className="w-4 h-4 group-hover:-translate-x-1 transition-transform" /> Back to Delivery
            </button>
            <div className="bg-white/80 backdrop-blur-xl p-8 sm:p-12 rounded-[2.5rem] shadow-xl border border-white/60">
              <h2 className="text-3xl font-black text-slate-900 mb-2 flex items-center gap-4"><ShieldCheck className="text-teal-600" /> Secure Payment</h2>
              <p className="text-slate-500 font-medium mb-8 pb-6 border-b border-slate-200">Amount to pay: <span className="text-2xl font-black text-slate-900">₹{totalAmount}</span></p>
              
              {checkoutError && <div className="mb-6 p-4 bg-red-50 text-red-600 font-bold rounded-xl border border-red-100">{checkoutError}</div>}
              
              <div className="space-y-4 mb-10">
                {[
                  { id: 'card', icon: <CreditCard />, title: 'Credit / Debit Card' },
                  { id: 'upi', icon: <Smartphone />, title: 'UPI Payment' },
                  { id: 'cod', icon: <Banknote />, title: 'Cash on Delivery' }
                ].map(method => (
                  <label key={method.id} className={`flex items-center gap-4 p-6 rounded-2xl border-2 cursor-pointer transition-all ${paymentMethod === method.id ? 'border-teal-500 bg-teal-50 shadow-sm' : 'border-slate-100 hover:border-teal-200 bg-white'}`}>
                    <div className={`p-3 rounded-xl ${paymentMethod === method.id ? 'bg-teal-500 text-white' : 'bg-slate-100 text-slate-500'}`}>{method.icon}</div>
                    <span className="font-bold text-lg text-slate-900 flex-grow">{method.title}</span>
                    <input type="radio" name="payment" value={method.id} className="hidden" onChange={(e) => setPaymentMethod(e.target.value)} />
                    <div className={`w-6 h-6 rounded-full border-2 flex items-center justify-center ${paymentMethod === method.id ? 'border-teal-500' : 'border-slate-300'}`}>
                      {paymentMethod === method.id && <div className="w-3 h-3 bg-teal-500 rounded-full" />}
                    </div>
                  </label>
                ))}
              </div>
              <button onClick={finalizeOrder} className="w-full py-5 rounded-xl font-bold bg-teal-500 text-slate-900 hover:bg-teal-400 transition-colors text-lg shadow-lg">
                Confirm Order
              </button>
            </div>
          </div>
        )}

        {view === 'success' && (
          <div className="max-w-xl mx-auto text-center py-20 animate-in zoom-in-95 duration-500">
            <CheckCircle className="text-teal-500 w-24 h-24 mx-auto mb-6" />
            <h2 className="text-4xl font-black text-slate-900 mb-4">Order Confirmed!</h2>
            <p className="text-slate-600 text-lg mb-8 font-medium">Thank you, <span className="font-bold text-teal-700">{addressData.name}</span>. Your medicines will be delivered to <span className="font-bold">{addressData.city}</span> shortly.</p>
            <button onClick={() => { 
                setView('shop'); setActiveSection('human'); setSearchQuery('');
                setAddressData({name: '', phone: '', street: '', pincode: '', city: 'Malayadipudur', state: 'Tamil Nadu', tag: 'home'});
              }} 
              className="px-8 py-4 rounded-xl font-bold bg-slate-900 text-white hover:bg-teal-600 transition-colors shadow-lg"
            >
              Return to Catalog
            </button>
          </div>
        )}
      </main>

      {}
      <footer className="bg-[#eef6fb] text-slate-600 py-12 md:py-16 mt-12 border-t border-blue-100 font-sans">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          
          <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8 md:gap-12 mb-12">
            
            {/* Column 1: Company */}
            <div>
              <h4 className="text-lg font-bold text-slate-800 mb-5">Company</h4>
              <ul className="space-y-3.5 text-sm font-medium">
                <li><a href="#" className="hover:text-blue-600 transition-colors">About Us</a></li>
                <li><a href="#" className="hover:text-blue-600 transition-colors">Health Article</a></li>
                <li><a href="#" className="hover:text-blue-600 transition-colors">Health Stories</a></li>
                <li><a href="#" className="hover:text-blue-600 transition-colors">Health Library</a></li>
                <li><a href="#" className="hover:text-blue-600 transition-colors">Diseases & Health Conditions</a></li>
                <li><a href="#" className="hover:text-blue-600 transition-colors">Ayurveda</a></li>
                <li><a href="#" className="hover:text-blue-600 transition-colors">Understanding Generic Medicines</a></li>
                <li><a href="#" className="hover:text-blue-600 transition-colors">All Medicines</a></li>
                <li><a href="#" className="hover:text-blue-600 transition-colors">All Brands</a></li>
                <li><a href="#" className="hover:text-blue-600 transition-colors">Need Help</a></li>
                <li><a href="#" onClick={(e) => {e.preventDefault(); setView('faq');}} className="hover:text-blue-600 transition-colors">FAQ</a></li>
                <li><a href="#" className="hover:text-blue-600 transition-colors">Security</a></li>
                <li><a href="#" className="hover:text-blue-600 transition-colors">Savings Calculator</a></li>
                <li><a href="#" className="hover:text-blue-600 transition-colors">Advertise with Us</a></li>
              </ul>
            </div>

            {/* Column 2: Social & Legal */}
            <div>
              <h4 className="text-lg font-bold text-slate-800 mb-5">Social</h4>
              <div className="flex gap-4 mb-10">
                <a href="#" className="bg-blue-600 text-white p-2 rounded-full hover:bg-blue-700 transition-colors">
                  <Instagram className="w-5 h-5" />
                </a>
                <a href="#" className="bg-blue-600 text-white p-2 rounded-full hover:bg-blue-700 transition-colors">
                  <Facebook className="w-5 h-5" />
                </a>
                <a href="#" className="bg-blue-600 text-white p-2 rounded-full hover:bg-blue-700 transition-colors">
                  <Youtube className="w-5 h-5" />
                </a>
                <a href="#" className="bg-blue-600 text-white p-2 rounded-full hover:bg-blue-700 transition-colors">
                  <Linkedin className="w-5 h-5" />
                </a>
              </div>
              
              <h4 className="text-lg font-bold text-slate-800 mb-5">Legal</h4>
              <ul className="space-y-3.5 text-sm font-medium">
                <li><a href="#" className="hover:text-blue-600 transition-colors">Terms & Conditions</a></li>
                <li><a href="#" className="hover:text-blue-600 transition-colors">Privacy Policy</a></li>
                <li><a href="#" className="hover:text-blue-600 transition-colors">Editorial Policy</a></li>
                <li><a href="#" className="hover:text-blue-600 transition-colors">Returns & Cancellations</a></li>
                <li><a href="#" className="hover:text-blue-600 transition-colors">Lowest Price Guarantee T&C</a></li>
              </ul>
            </div>

            {/* Column 3: Subscribe & Address */}
            <div>
              <h4 className="text-lg font-bold text-slate-800 mb-3">Subscribe</h4>
              <p className="text-sm mb-4 leading-relaxed">Claim your complimentary health and fitness tips subscription and stay updated on our newest promotions.</p>
              <div className="flex bg-white rounded-lg overflow-hidden border border-slate-200 mb-8 shadow-sm">
                <input type="email" placeholder="Enter your email ID" className="px-4 py-3 w-full outline-none text-sm placeholder:text-slate-400 font-medium" />
                <button className="bg-blue-600 hover:bg-blue-700 transition-colors text-white px-5 py-3 text-sm font-bold">Subscribe</button>
              </div>
              
              <h4 className="text-lg font-bold text-slate-800 mb-3">Registered Office Address</h4>
              <p className="text-sm mb-1 font-bold">Parijatha Pharmaceuticals</p>
              <p className="text-sm mb-3 leading-relaxed">No 4, Devi Complex, Five Roads,<br/>Salem, Tamil Nadu, India, 636 004.</p>
              <p className="text-sm font-bold mb-8">Telephone: <a href="tel:9080386396" className="text-blue-600 font-black">9080386396</a></p>

              <h4 className="text-lg font-bold text-slate-800 mb-3">Grievance Officer</h4>
              <p className="text-sm font-medium mb-1">Name: Prashanth</p>
              <p className="text-sm font-medium">Email: <a href="mailto:ppprashanth13@yahoo.com" className="text-blue-600 font-bold">ppprashanth13@yahoo.com</a></p>
            </div>

            {/* Column 4: Download & Contact */}
            <div>
               <h4 className="text-lg font-bold text-slate-800 mb-3">Download Parijatha App</h4>
               <p className="text-sm mb-2 font-medium">Manage your health with ease.</p>
               <p className="text-sm mb-4 leading-relaxed">Get easy access to medicine refills, health information, and more. Download now and start taking control of your health.</p>
               <div className="flex gap-3 mb-10 flex-wrap">
                 <button className="flex items-center gap-2 bg-black text-white px-4 py-2 rounded-lg hover:bg-slate-800 transition-colors">
                   <Play className="w-5 h-5" />
                   <div className="text-left">
                     <div className="text-[9px] uppercase tracking-wider">Get it on</div>
                     <div className="text-sm font-bold leading-none">Google Play</div>
                   </div>
                 </button>
                 <button className="flex items-center gap-2 bg-black text-white px-4 py-2 rounded-lg hover:bg-slate-800 transition-colors">
                   <Apple className="w-5 h-5" />
                   <div className="text-left">
                     <div className="text-[9px] uppercase tracking-wider">Download on the</div>
                     <div className="text-sm font-bold leading-none">App Store</div>
                   </div>
                 </button>
               </div>
               
               <h4 className="text-lg font-bold text-slate-800 mb-3">Contact Us</h4>
               <p className="text-sm mb-4 leading-relaxed font-medium">Our customer representative team is available 7 days a week from 9:00 am - 10:00 pm.</p>
               <div className="flex justify-between items-center text-sm mb-4">
                  <a href="mailto:ppprashanth13@yahoo.com" className="font-bold text-slate-700 hover:text-blue-600 transition-colors">ppprashanth13@yahoo.com</a>
                  <a href="tel:9080386396" className="font-black text-slate-700 hover:text-blue-600 transition-colors">9080386396</a>
               </div>
               <p className="text-xs text-slate-400 font-bold">v1.0.0</p>
            </div>
            
          </div>
          
          <div className="flex flex-col md:flex-row justify-between items-center pt-8 border-t border-blue-200/60 text-xs text-slate-500 gap-4">
             <div className="flex items-center gap-4">
               <span className="font-bold">© 2026 Parijatha Pharmaceuticals | All rights reserved.</span>
               <span className="hidden md:inline">Our content is for informational purposes only.</span>
             </div>
             
             <div className="flex flex-wrap items-center justify-center gap-6">
                <span className="font-bold text-slate-400">Our Payment Partners</span>
                <div className="flex items-center gap-3">
                  <span className="font-black italic text-blue-800 text-sm">VISA</span>
                  <span className="font-bold text-red-600 text-sm">Mastercard</span>
                  <span className="font-black italic text-orange-600 text-sm">UPI</span>
                  <span className="font-bold text-sky-500 text-sm">Paytm</span>
                  <span className="font-bold text-slate-700 text-sm">GPay</span>
                </div>
             </div>
          </div>

        </div>
      </footer>
    </div>
  );
}
